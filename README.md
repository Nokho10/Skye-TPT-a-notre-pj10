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
// se code est a mettre dans event  Create
move_speed = 4;
jump_force = -10;
grav = 0.5;
vsp = 0;


// Déplacement gauche / droite
var move = keyboard_check(vk_right) - keyboard_check(vk_left);
x += move * move_speed;


// Gravité
vsp += grav;
y += vsp;

// Collision sol (remplace obj_sol par ton objet sol)
if (place_meeting(x, y + 1, obj_sol))
{
    while (!place_meeting(x, y, obj_sol))
    {
        y += 1;
    }
    vsp = 0;

    // Saut seulement si au sol
    if (keyboard_check_pressed(vk_space))
    {
        vsp = jump_force;
    }
}
