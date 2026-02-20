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
