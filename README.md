# Skye-TPT-a-notre-pj10
Bienvenue sur le Github de notre projet "Skye" nom non definitvie
Se Github a pour bute d'échange et planifier se projet (code , bug , asset ect...)
Il faudra alors mettre ici se que tu a fais et si ta un probleme
[NIVEAUX- Tuto- sous terre- NIVEAUX 2-terre- NIVEAUX 3- Ciel]
EXEMPLE
              _______<sujet>_____
                code/asset/->


              ___________________
                Probleme rencontre et si tu as résolutions

--tache---
[X] Sprite MC
[X] Background ciel
[X] sol roche
[X] sol terre
[] sol "nuage"
[X]echelle
[] pnj lore
[X]crée les doss frame MC
--------------------------------------

code_______
// a mettre dans Event ->create
hsp = 0;
vsp = 0;

walk_speed = 4;
grav = 0.5;
jump_power = -10;
//a mettre dans Event step du player

// ----- INPUT GAUCHE / DROITE -----
hsp = 0;

if (keyboard_check(ord("Q")))
{
    hsp = -walk_speed;
}

if (keyboard_check(ord("D")))
{
    hsp = walk_speed;
}


// ----- COLLISION HORIZONTALE -----
if (place_meeting(x + hsp, y, obj_sol))
{
    while (!place_meeting(x + sign(hsp), y, obj_sol))
    {
        x += sign(hsp);
    }
    hsp = 0;
}

x += hsp;


// ----- GRAVITÉ -----
vsp += grav;


// ----- SAUT -----
if (keyboard_check_pressed(vk_space))
{
    if (place_meeting(x, y + 1, obj_sol))
    {
        vsp = jump_power;
    }
}


// ----- COLLISION VERTICALE -----
if (place_meeting(x, y + vsp, obj_sol))
{
    while (!place_meeting(x, y + sign(vsp), obj_sol))
    {
        y += sign(vsp);
    }
    vsp = 0;
}
else
{
    y += vsp;
}







----code brouillon------
//✅ 1️⃣ Dans le Create Event du joueur

//Ajoute ça :

max_hp = 100;
hp = max_hp;
//✅ 2️⃣ Pour perdre de la vie (exemple)

//Par exemple si tu touches un ennemi :

hp -= 10;

//Si tu veux tester vite fait, mets dans Step :

if (keyboard_check_pressed(ord("H")))
{
    hp -= 10;
}

//Appuie sur H → tu perds 10 HP.

//✅ 3️⃣ Empêcher les HP négatifs

//Toujours dans Step :

if (hp < 0)
{
    hp = 0;
}
//✅ 4️⃣ Afficher une barre de vie

//Ajoute un Draw GUI Event à obj_player.

//Mets ça dedans :

// Fond de barre
draw_set_color(c_black);
draw_rectangle(20, 20, 220, 40, false);

// Barre rouge
var hp_ratio = hp / max_hp;

draw_set_color(c_red);
draw_rectangle(20, 20, 20 + (200 * hp_ratio), 40, false);

// Texte
draw_set_color(c_white);
draw_text(25, 22, "HP: " + string(hp));
//🎯 Résultat
-------------------
✔ Barre noire = fond
✔ Rouge = vie actuelle
✔ Texte HP

💡 Si tu veux que le joueur meure

Ajoute dans Step :

if (hp <= 0)
{
    show_message("GAME OVER");
    instance_destroy();
}
