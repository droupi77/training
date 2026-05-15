import { useState, useEffect, useCallback, useRef } from "react";

// ─── STORAGE ──────────────────────────────────────────────────────────────────
// localStorage — données persistantes par utilisateur, par navigateur
function useStorage(key, init) {
  const [val, setVal] = useState(() => {
    try { const s = localStorage.getItem(key); return s ? JSON.parse(s) : init; } catch { return init; }
  });
  const ref = useRef(val);
  const set = useCallback(fn => {
    const v = typeof fn === "function" ? fn(ref.current) : fn;
    ref.current = v; setVal(v);
    try { localStorage.setItem(key, JSON.stringify(v)); } catch {}
  }, [key]);
  return [val, set];
}

// ─── TABLES DE REPS ───────────────────────────────────────────────────────────
// Validées scientifiquement (Schoenfeld 2017) — diff par type d'exercice et sexe
const RT = {
  compound_heavy:     { force:"3-5",  hypertrophie:"8-10",  endurance:"10-12" },
  compound_secondary: { force:"4-6",  hypertrophie:"6-10",  endurance:"10-12" },
  poly_isolation:     { force:"6-8",  hypertrophie:"8-12",  endurance:"12-15" },
  isolation:          { force:"8-10", hypertrophie:"12-15", endurance:"15-20" },
};
// Femme : +1-2 reps (fibres type I, tolérance volume supérieure — Schoenfeld 2020)
const RTF = {
  compound_heavy:     { force:"4-6",   hypertrophie:"8-10",  endurance:"12-15" },
  compound_secondary: { force:"5-8",   hypertrophie:"8-12",  endurance:"12-15" },
  poly_isolation:     { force:"8-10",  hypertrophie:"10-14", endurance:"14-18" },
  isolation:          { force:"10-12", hypertrophie:"14-17", endurance:"17-22" },
};

const CATALOGUE = {
  Pectoraux: [
    { name:"Développé couché barre",           et:"compound_heavy",     loc:"gym",  f:"Sterno-costal - Milieu",   note:"Exercice roi de masse pec. Surcharge progressive illimitée",                gif:"https://media.tenor.com/hbMFmAHfaYsAAAAd/bench-press-chest.gif",         alts:["Développé couché haltères","Chest press machine"] },
    { name:"Développé incliné 30 haltères",    et:"compound_secondary", loc:"gym",  f:"Claviculaire - Haut",      note:"30 degrés = angle optimal haut du pec. Amplitude supérieure à la barre",   gif:"https://media.tenor.com/V_4CmPFKrjQAAAAd/incline-bench-press.gif",        alts:["Développé incliné barre","Pompes pieds surélevés"] },
    { name:"Dips buste incliné pectoraux",     et:"compound_secondary", loc:"gym",  f:"Costal - Bas",             note:"Seul composé lourd ciblant vraiment le bas du pec. Lestable",              gif:"https://media.tenor.com/jSk9nNuCGGoAAAAd/dips-triceps.gif",               alts:["Développé décliné haltères","Écarté poulie haute descendant"] },
    { name:"Écarté poulie basse montant",      et:"isolation",          loc:"gym",  f:"Claviculaire - Haut",      note:"Tension constante sur le haut du pec. Supérieur aux écartés haltères",     gif:"https://media.tenor.com/qIFDesO5PXMAAAAC/dumbbell-flyes-chest.gif",       alts:["Crossover poulie basse","Développé incliné 30 haltères"] },
    { name:"Écarté poulie haute descendant",   et:"isolation",          loc:"gym",  f:"Costal - Bas",             note:"Isolation bas du pec en tension constante. Parfait en finition",           gif:"https://media.tenor.com/qIFDesO5PXMAAAAC/dumbbell-flyes-chest.gif",       alts:["Dips buste incliné pectoraux","Développé décliné haltères"] },
    { name:"Développé couché haltères",        et:"compound_secondary", loc:"gym",  f:"Sterno-costal - Milieu",   note:"Amplitude supérieure à la barre. Favorable pour les épaules fragiles",     gif:"https://media.tenor.com/hbMFmAHfaYsAAAAd/bench-press-chest.gif",         alts:["Développé couché barre","Chest press machine"] },
    { name:"Pompes classiques",                et:"compound_heavy",     loc:"home", f:"Sterno-costal - Milieu",   note:"Base maison. Progresser : tempo 4s descente, pause basse 2s",             gif:"https://media.tenor.com/hbMFmAHfaYsAAAAd/bench-press-chest.gif",         alts:["Pompes pieds surélevés","Dips entre deux chaises"] },
    { name:"Pompes pieds surélevés",           et:"compound_secondary", loc:"home", f:"Claviculaire - Haut",      note:"Pieds sur chaise = angle incliné, recrutement claviculaire supérieur",     gif:"https://media.tenor.com/hbMFmAHfaYsAAAAd/bench-press-chest.gif",         alts:["Pompes classiques","Pompes déclinées"] },
    { name:"Pompes déclinées",                 et:"compound_secondary", loc:"home", f:"Costal - Bas",             note:"Mains sur chaise = angle décliné, cible le bas du pec",                   gif:"https://media.tenor.com/hbMFmAHfaYsAAAAd/bench-press-chest.gif",         alts:["Dips entre deux chaises","Pompes classiques"] },
    { name:"Dips entre deux chaises",          et:"compound_secondary", loc:"home", f:"Costal - Bas",             note:"Buste incliné vers l'avant = focus pec bas. Deux chaises stables",         gif:"https://media.tenor.com/jSk9nNuCGGoAAAAd/dips-triceps.gif",               alts:["Pompes déclinées","Pompes classiques"] },
  ],
  Dos: [
    { name:"Tractions pronation large",        et:"compound_heavy",     loc:"gym",  f:"Grand Dorsal - Largeur",   note:"Exercice roi du dos en largeur. Lestage progressif = gains illimités",     gif:"https://media.tenor.com/GjFMHkGFNxsAAAAd/pull-up-workout.gif",            alts:["Tirage poulie haute prise large","Tirage poulie haute prise neutre"] },
    { name:"Rowing barre pronation",           et:"compound_heavy",     loc:"gym",  f:"Haut du Dos - Épaisseur",  note:"Volume et masse en épaisseur. Recrutement trapèze + rhomboïdes",          gif:"https://media.tenor.com/TjuvSSUMaKsAAAAd/barbell-row-back.gif",            alts:["Rowing haltère unilatéral","Rowing machine assis"] },
    { name:"Extensions banc 45",              et:"poly_isolation",      loc:"gym",  f:"Érecteurs - Bas du dos",   note:"Santé lombaire indispensable. Peut être lesté pour hypertrophie",          gif:"https://media.tenor.com/d9yGbIHrOSsAAAAd/deadlift-back.gif",              alts:["Good mornings barre","Superman au sol"] },
    { name:"Tirage poulie haute prise neutre", et:"compound_secondary", loc:"gym",  f:"Grand Dorsal - Largeur",   note:"Grand dorsal bas en tension maximale en fin de course",                    gif:"https://media.tenor.com/5Ge0FNPpnZIAAAAd/lat-pulldown-back.gif",          alts:["Tractions supination","Tractions pronation large"] },
    { name:"Rowing haltère unilatéral",        et:"compound_secondary", loc:"gym",  f:"Haut du Dos - Épaisseur",  note:"Amplitude supérieure à la barre. Corrige les déséquilibres gauche droite",  gif:"https://media.tenor.com/JB1C1HFTL9gAAAAd/one-arm-dumbbell-row.gif",      alts:["Rowing machine assis","Rowing barre pronation"] },
    { name:"Pull-over poulie haute",           et:"isolation",          loc:"gym",  f:"Grand Dorsal - Largeur",   note:"Élongation maximale du grand dorsal. Souvent négligé, très efficace",      gif:"https://media.tenor.com/5Ge0FNPpnZIAAAAd/lat-pulldown-back.gif",          alts:["Pull-over haltère","Tirage poulie haute prise neutre"] },
    { name:"Rowing machine assis prise large", et:"poly_isolation",     loc:"gym",  f:"Haut du Dos - Épaisseur",  note:"Coudes à 45-60 degrés = recrutement optimal rhomboïdes et trapèze moyen",  gif:"https://media.tenor.com/JB1C1HFTL9gAAAAd/one-arm-dumbbell-row.gif",      alts:["Rowing haltère unilatéral","Rowing barre pronation"] },
    { name:"Tractions prise large maison",     et:"compound_heavy",     loc:"home", f:"Grand Dorsal - Largeur",   note:"Barre de porte environ 15 euros. Exercice roi du dos maison",              gif:"https://media.tenor.com/GjFMHkGFNxsAAAAd/pull-up-workout.gif",            alts:["Tractions supination maison","Tirage horizontal sous table"] },
    { name:"Tractions supination maison",      et:"compound_heavy",     loc:"home", f:"Grand Dorsal - Largeur",   note:"Prise supination sur barre de porte. Plus de biceps recruté",              gif:"https://media.tenor.com/GjFMHkGFNxsAAAAd/pull-up-workout.gif",            alts:["Tractions prise large maison","Tirage horizontal sous table"] },
    { name:"Tirage horizontal sous table",     et:"compound_secondary", loc:"home", f:"Haut du Dos - Épaisseur",  note:"Allongé sous table solide, attrape le bord et tire. Imite le rowing",      gif:"https://media.tenor.com/JB1C1HFTL9gAAAAd/one-arm-dumbbell-row.gif",      alts:["Rowing haltère léger","Tractions prise large maison"] },
    { name:"Rowing haltère léger",             et:"compound_secondary", loc:"home", f:"Haut du Dos - Épaisseur",  note:"6-8kg. Même mouvement qu'en salle. Genou sur chaise, dos plat",            gif:"https://media.tenor.com/JB1C1HFTL9gAAAAd/one-arm-dumbbell-row.gif",      alts:["Tirage horizontal sous table","Tractions prise large maison"] },
    { name:"Superman au sol",                  et:"poly_isolation",     loc:"home", f:"Érecteurs - Bas du dos",   note:"Allongé face au sol, soulever bras et jambes. Tenir 3 secondes",           gif:"https://media.tenor.com/d9yGbIHrOSsAAAAd/deadlift-back.gif",              alts:["Extensions banc 45","Good mornings barre"] },
  ],
  Épaules: [
    { name:"Développé militaire barre",        et:"compound_heavy",     loc:"gym",  f:"Deltoïde Antérieur",       note:"Force brute. Renforce tout le tronc par stabilisation",                   gif:"https://media.tenor.com/5n1bJfbixNMAAAAd/overhead-press-shoulders.gif",  alts:["Développé militaire haltères","Arnold press"] },
    { name:"Développé militaire haltères",     et:"compound_secondary", loc:"gym",  f:"Deltoïde Antérieur",       note:"Liberté articulaire plus grande. Meilleur pour les épaules fragiles",     gif:"https://media.tenor.com/5n1bJfbixNMAAAAd/overhead-press-shoulders.gif",  alts:["Développé militaire barre","Arnold press"] },
    { name:"Élévations latérales poulie",      et:"isolation",          loc:"gym",  f:"Deltoïde Latéral",         note:"Tension constante sur tout l'arc. Principal responsable de la largeur",   gif:"https://media.tenor.com/lPCuRpU4GgUAAAAd/lateral-raise-shoulders.gif",   alts:["Élévations latérales haltères","Élévations latérales machine"] },
    { name:"Élévations latérales haltères",    et:"isolation",          loc:"gym",  f:"Deltoïde Latéral",         note:"Contrôle strict obligatoire. Essentiel pour la largeur épaule",           gif:"https://media.tenor.com/lPCuRpU4GgUAAAAd/lateral-raise-shoulders.gif",   alts:["Élévations latérales poulie","Élévations latérales machine"] },
    { name:"Face pull poulie corde",           et:"isolation",          loc:"gym",  f:"Deltoïde Postérieur",      note:"OBLIGATOIRE. Santé coiffe rotateurs + faisceau post. Prévient blessures",  gif:"https://media.tenor.com/x6XbBpQzRnQAAAAd/face-pull-shoulders.gif",      alts:["Reverse fly pec deck","Oiseau haltères penché"] },
    { name:"Oiseau haltères penché",           et:"isolation",          loc:"gym",  f:"Deltoïde Postérieur",      note:"Isolation faisceau postérieur. Essentiel contre la cyphose",              gif:"https://media.tenor.com/x6XbBpQzRnQAAAAd/face-pull-shoulders.gif",      alts:["Face pull poulie corde","Reverse fly pec deck"] },
    { name:"Pike push-up",                     et:"compound_secondary", loc:"home", f:"Deltoïde Antérieur",       note:"Pompes en V inversé, hanches hautes. Cible fortement le deltoïde ant.",   gif:"https://media.tenor.com/5n1bJfbixNMAAAAd/overhead-press-shoulders.gif",  alts:["Développé épaules haltères légers","Handstand push-up mur"] },
    { name:"Développé épaules haltères légers",et:"compound_secondary", loc:"home", f:"Deltoïde Antérieur",       note:"6-8kg assis ou debout. Mouvement complet overhead",                       gif:"https://media.tenor.com/5n1bJfbixNMAAAAd/overhead-press-shoulders.gif",  alts:["Pike push-up","Élévations frontales haltères légers"] },
    { name:"Élévations latérales légers",      et:"isolation",          loc:"home", f:"Deltoïde Latéral",         note:"4-6kg. Technique stricte. Poids léger force le contrôle",                 gif:"https://media.tenor.com/lPCuRpU4GgUAAAAd/lateral-raise-shoulders.gif",   alts:["Élévations latérales haltères","Pike push-up"] },
    { name:"Oiseau haltères légers penché",    et:"isolation",          loc:"home", f:"Deltoïde Postérieur",      note:"OBLIGATOIRE maison. 4-6kg. Prévient douleurs épaule et cyphose posturale", gif:"https://media.tenor.com/x6XbBpQzRnQAAAAd/face-pull-shoulders.gif",      alts:["Oiseau haltères penché","Face pull élastique"] },
  ],
  Biceps: [
    { name:"Curl incliné haltères",            et:"isolation", loc:"gym",  f:"Chef Long - Peak",       note:"Position inclinée = étirement maximal chef long. Meilleur pour le pic",    gif:"https://media.tenor.com/YqWGVVBRsHkAAAAd/dumbbell-curl-biceps.gif",        alts:["Drag curl barre","Curl poulie basse"] },
    { name:"Drag curl barre",                  et:"isolation", loc:"gym",  f:"Chef Long - Peak",       note:"Coude derrière le corps = tension maximale chef long en permanence",        gif:"https://media.tenor.com/6KMSOaI6XHQAAAAC/barbell-curl-biceps.gif",         alts:["Curl incliné haltères","Curl barre EZ"] },
    { name:"Spider curl banc incliné",         et:"isolation", loc:"gym",  f:"Chef Court - Épaisseur", note:"Coude devant = isolation totale chef court. Aucune triche possible",        gif:"https://media.tenor.com/YqWGVVBRsHkAAAAd/dumbbell-curl-biceps.gif",        alts:["Curl pupitre Scott","Preacher curl machine"] },
    { name:"Curl pupitre Scott",               et:"isolation", loc:"gym",  f:"Chef Court - Épaisseur", note:"Pupitre supprime la flexion du tronc. Isolation pure du biceps brachii",    gif:"https://media.tenor.com/YqWGVVBRsHkAAAAd/dumbbell-curl-biceps.gif",        alts:["Spider curl banc incliné","Preacher curl machine"] },
    { name:"Curl marteau haltères",            et:"isolation", loc:"gym",  f:"Brachial - Avant-bras",  note:"Prise neutre cible le brachial antérieur. Donne épaisseur au bras",         gif:"https://media.tenor.com/LKP2GgcrxBEAAAAd/hammer-curl-biceps.gif",          alts:["Reverse curl barre EZ","Curl marteau câble"] },
    { name:"Curl haltères légers alterné",     et:"isolation", loc:"home", f:"Chef Long - Peak",       note:"6-8kg en alterné avec rotation en supination",                             gif:"https://media.tenor.com/YqWGVVBRsHkAAAAd/dumbbell-curl-biceps.gif",        alts:["Curl incliné haltères légers","Curl isométrique serviette"] },
    { name:"Curl incliné haltères légers",     et:"isolation", loc:"home", f:"Chef Long - Peak",       note:"Assis sur bord de chaise. 6-8kg. Étirement chef long maximal",              gif:"https://media.tenor.com/YqWGVVBRsHkAAAAd/dumbbell-curl-biceps.gif",        alts:["Curl haltères légers alterné","Curl isométrique serviette"] },
    { name:"Curl marteau haltères légers",     et:"isolation", loc:"home", f:"Brachial - Avant-bras",  note:"6-8kg prise neutre. Brachial antérieur. Épaisseur du bras",                 gif:"https://media.tenor.com/LKP2GgcrxBEAAAAd/hammer-curl-biceps.gif",          alts:["Curl haltères légers alterné","Curl isométrique serviette"] },
    { name:"Curl isométrique serviette",       et:"isolation", loc:"home", f:"Chef Court - Épaisseur", note:"Pied sur serviette, tirer vers le haut. Résistance = poids corps",          gif:"https://media.tenor.com/YqWGVVBRsHkAAAAd/dumbbell-curl-biceps.gif",        alts:["Curl haltères légers alterné","Curl marteau haltères légers"] },
  ],
  Triceps: [
    { name:"Extension overhead poulie",        et:"isolation",          loc:"gym",  f:"Chef Long - OVERHEAD",  note:"Maeo 2022 : +40% hypertrophie vs position neutre. Chef long en étirement max", gif:"https://media.tenor.com/cHXhPLFBvusAAAAd/tricep-pushdown-triceps.gif",   alts:["French press barre EZ","Extension overhead haltère"] },
    { name:"French press barre EZ",            et:"compound_secondary", loc:"gym",  f:"Chef Long - OVERHEAD",  note:"Chef long en stretch profond. Charge lourde pour masse triceps",              gif:"https://media.tenor.com/b0v2LxmDVlsAAAAd/skull-crusher-triceps.gif",     alts:["Extension overhead poulie","Extension overhead haltère"] },
    { name:"Pushdown corde prise neutre",      et:"isolation",          loc:"gym",  f:"Chef Latéral et Médial",note:"Rotation externe en bas = contraction maximale chef latéral",                gif:"https://media.tenor.com/cHXhPLFBvusAAAAd/tricep-pushdown-triceps.gif",   alts:["Pushdown barre droite","Kickback câble"] },
    { name:"Pushdown barre droite",            et:"isolation",          loc:"gym",  f:"Chef Latéral et Médial",note:"Charge plus lourde que la corde. Cible chef latéral",                         gif:"https://media.tenor.com/cHXhPLFBvusAAAAd/tricep-pushdown-triceps.gif",   alts:["Pushdown corde prise neutre","Kickback câble"] },
    { name:"Développé couché prise serrée",    et:"compound_secondary", loc:"gym",  f:"Composé - Masse globale",note:"Plus chargeable de tous les exos triceps. Masse globale",                    gif:"https://media.tenor.com/hbMFmAHfaYsAAAAd/bench-press-chest.gif",         alts:["Dips verticaux triceps","Close grip Smith Machine"] },
    { name:"Extension overhead haltère",       et:"isolation",          loc:"home", f:"Chef Long - OVERHEAD",  note:"OBLIGATOIRE maison. 6-8kg. Chef long en étirement maximal",                  gif:"https://media.tenor.com/cHXhPLFBvusAAAAd/tricep-pushdown-triceps.gif",   alts:["Extension overhead 1 bras","Pompes diamant"] },
    { name:"Extension overhead 1 bras",        et:"isolation",          loc:"home", f:"Chef Long - OVERHEAD",  note:"6-8kg d'un bras. Amplitude encore plus grande",                              gif:"https://media.tenor.com/cHXhPLFBvusAAAAd/tricep-pushdown-triceps.gif",   alts:["Extension overhead haltère","Pompes diamant"] },
    { name:"Dips entre chaises triceps",       et:"compound_secondary", loc:"home", f:"Composé - Masse globale",note:"Corps droit = focus triceps. Deux chaises stables",                          gif:"https://media.tenor.com/jSk9nNuCGGoAAAAd/dips-triceps.gif",               alts:["Pompes diamant","Extension overhead haltère"] },
    { name:"Pompes diamant",                   et:"compound_secondary", loc:"home", f:"Chef Latéral et Médial",note:"Prise triangulaire = triceps fortement sollicité. Sans matériel",             gif:"https://media.tenor.com/jSk9nNuCGGoAAAAd/dips-triceps.gif",               alts:["Dips entre chaises triceps","Extension overhead haltère"] },
  ],
  Quadriceps: [
    { name:"Squat barre haute",                et:"compound_heavy",     loc:"gym",  f:"Vastes - Composé lourd", note:"Exercice roi du bas du corps. Recrutement global quad + fessiers + core",  gif:"https://media.tenor.com/qnMOG5UGiEkAAAAd/squat-legs.gif",                alts:["Hack squat machine","Fentes bulgares haltères"] },
    { name:"Hack squat machine",               et:"compound_heavy",     loc:"gym",  f:"Vastes - Composé lourd", note:"Isole mieux les vastes que le squat barre. Moins de stress lombaire",      gif:"https://media.tenor.com/jLKq2MAHl8gAAAAd/leg-press-quads.gif",            alts:["Squat barre haute","Presse cuisses pieds bas"] },
    { name:"Presse cuisses pieds bas",         et:"poly_isolation",     loc:"gym",  f:"Vastes - Secondaire",    note:"Pieds bas et serrés = focus vastes externes. Sans charge axiale",           gif:"https://media.tenor.com/jLKq2MAHl8gAAAAd/leg-press-quads.gif",            alts:["Hack squat machine","Fentes bulgares haltères"] },
    { name:"Leg extension machine",            et:"isolation",          loc:"gym",  f:"Rectus Femoris - ISO",   note:"SEUL exercice isolant le rectus femoris biarticulaire. Indispensable",      gif:"https://media.tenor.com/jLKq2MAHl8gAAAAd/leg-press-quads.gif",            alts:["Leg extension unilatéral","Fentes pied avant surélevé"] },
    { name:"Fentes bulgares haltères",         et:"compound_secondary", loc:"gym",  f:"Unilatéral - Amplitude", note:"Amplitude maximale. Corrige déséquilibres. Fort recrutement quadri + fessier", gif:"https://media.tenor.com/xTxGJpnMLPcAAAAd/lunges-legs.gif",               alts:["Fentes marchées haltères","Step up haltères"] },
    { name:"Squat bulgare poids de corps",     et:"compound_heavy",     loc:"home", f:"Vastes - Composé lourd", note:"Pied arrière sur chaise. Très intense sans charge. Meilleur exo quad maison", gif:"https://media.tenor.com/xTxGJpnMLPcAAAAd/lunges-legs.gif",               alts:["Squat profond poids de corps","Fentes marchées"] },
    { name:"Squat profond poids de corps",     et:"compound_heavy",     loc:"home", f:"Vastes - Composé lourd", note:"Descente maximale, talon au sol. Progresser en tempo lent 4s",              gif:"https://media.tenor.com/qnMOG5UGiEkAAAAd/squat-legs.gif",                alts:["Squat bulgare poids de corps","Squat sauté"] },
    { name:"Fentes marchées",                  et:"compound_secondary", loc:"home", f:"Unilatéral - Amplitude", note:"Unilatéral sans matériel. Quad + fessiers + équilibre",                    gif:"https://media.tenor.com/xTxGJpnMLPcAAAAd/lunges-legs.gif",                alts:["Squat bulgare poids de corps","Squat profond poids de corps"] },
    { name:"Squat sauté",                      et:"compound_secondary", loc:"home", f:"Vastes - Secondaire",    note:"Explosion vers le haut depuis position squat. Puissance + endurance",       gif:"https://media.tenor.com/qnMOG5UGiEkAAAAd/squat-legs.gif",                alts:["Squat profond poids de corps","Fentes sautées"] },
    { name:"Fentes avant pied surélevé",       et:"isolation",          loc:"home", f:"Rectus Femoris - ISO",   note:"Pied avant sur marche. Genou dépasse le pied = rectus femoris maximal",     gif:"https://media.tenor.com/xTxGJpnMLPcAAAAd/lunges-legs.gif",                alts:["Squat bulgare poids de corps","Fentes marchées"] },
  ],
  Ischio: [
    { name:"SDT roumain barre",                et:"compound_heavy",     loc:"gym",  f:"Hip Hinge - Étiré",      note:"Ischio en élongation maximale. Indispensable avec leg curl assis",          gif:"https://media.tenor.com/d9yGbIHrOSsAAAAd/deadlift-back.gif",              alts:["SDT roumain haltères","Good mornings barre"] },
    { name:"Leg curl assis machine",           et:"isolation",          loc:"gym",  f:"Leg Curl - Priorité",    note:"Maeo 2021 : +14% hypertrophie vs couché. Hanche fléchie = étirement max",   gif:"https://media.tenor.com/YMxVvkiRtHsAAAAd/leg-curl-hamstrings.gif",        alts:["Leg curl couché machine","Nordic curl"] },
    { name:"Leg curl couché machine",          et:"isolation",          loc:"gym",  f:"Leg Curl - Complémentaire",note:"Bonne activation biceps femoris court. Complément du leg curl assis",    gif:"https://media.tenor.com/YMxVvkiRtHsAAAAd/leg-curl-hamstrings.gif",        alts:["Leg curl assis machine","Nordic curl"] },
    { name:"Good mornings barre",              et:"compound_secondary", loc:"gym",  f:"Hip Hinge - Étiré",      note:"Renforce érecteurs + ischio simultanément. Attention à la technique",       gif:"https://media.tenor.com/d9yGbIHrOSsAAAAd/deadlift-back.gif",              alts:["SDT roumain haltères","SDT roumain barre"] },
    { name:"SDT roumain haltères légers",      et:"compound_secondary", loc:"home", f:"Hip Hinge - Étiré",      note:"2x8kg max. Même stimulus que barre. Dos plat, bien étirer les ischio",      gif:"https://media.tenor.com/d9yGbIHrOSsAAAAd/deadlift-back.gif",              alts:["Bonne nuit poids de corps","Nordic curl"] },
    { name:"Nordic curl",                      et:"compound_secondary", loc:"home", f:"Leg Curl - Priorité",    note:"Pieds bloqués sous canapé. Descente excentrique lente. Très efficace",       gif:"https://media.tenor.com/YMxVvkiRtHsAAAAd/leg-curl-hamstrings.gif",        alts:["SDT roumain haltères légers","Ischio curl serviette"] },
    { name:"Ischio curl serviette",            et:"isolation",          loc:"home", f:"Leg Curl - Complémentaire",note:"Talon sur serviette sur sol lisse. Fléchir en tirant. Sans matériel",    gif:"https://media.tenor.com/YMxVvkiRtHsAAAAd/leg-curl-hamstrings.gif",        alts:["Nordic curl","SDT roumain haltères légers"] },
    { name:"Bonne nuit poids de corps",        et:"compound_secondary", loc:"home", f:"Hip Hinge - Étiré",      note:"Inclinaison buste dos droit. Étire ischio sans charge",                    gif:"https://media.tenor.com/d9yGbIHrOSsAAAAd/deadlift-back.gif",              alts:["SDT roumain haltères légers","Nordic curl"] },
  ],
  Fessiers: [
    { name:"Hip thrust barre",                 et:"compound_secondary", loc:"gym",  f:"Grand Fessier - Force",  note:"Exercice roi fessiers. Position raccourcie = charge maximale",             gif:"https://media.tenor.com/A5EMCkBEFvYAAAAd/hip-thrust-glutes.gif",          alts:["Hip thrust machine","Pont fessier lesté"] },
    { name:"Fentes bulgares fessiers",         et:"compound_secondary", loc:"gym",  f:"Grand Fessier - Amplitude",note:"Amplitude maximale = grand fessier en étirement profond",                gif:"https://media.tenor.com/xTxGJpnMLPcAAAAd/lunges-legs.gif",                alts:["Fentes marchées haltères","Step up haltères"] },
    { name:"Abduction hanche machine",         et:"isolation",          loc:"gym",  f:"Moyen Fessier - Stabilité",note:"Moyen fessier négligé = instabilité genou/bassin. Essentiel",            gif:"https://media.tenor.com/A5EMCkBEFvYAAAAd/hip-thrust-glutes.gif",          alts:["Abduction poulie basse","Monster walk élastique"] },
    { name:"Hip thrust machine",               et:"compound_secondary", loc:"gym",  f:"Grand Fessier - Force",  note:"Version guidée. Charge parfaitement reproductible et progressive",         gif:"https://media.tenor.com/A5EMCkBEFvYAAAAd/hip-thrust-glutes.gif",          alts:["Hip thrust barre","Pont fessier lesté"] },
    { name:"Kickback câble",                   et:"isolation",          loc:"gym",  f:"Grand Fessier - Isolation",note:"Isole le chef inférieur du grand fessier en extension de hanche pure",   gif:"https://media.tenor.com/A5EMCkBEFvYAAAAd/hip-thrust-glutes.gif",          alts:["Kickback machine","Abduction hanche machine"] },
    { name:"Pont fessier unilatéral",          et:"compound_secondary", loc:"home", f:"Grand Fessier - Force",  note:"Allongé au sol, une jambe levée, pousser fort. Double l'intensité",        gif:"https://media.tenor.com/A5EMCkBEFvYAAAAd/hip-thrust-glutes.gif",          alts:["Pont fessier lesté","Hip thrust entre chaises"] },
    { name:"Pont fessier lesté",               et:"compound_secondary", loc:"home", f:"Grand Fessier - Force",  note:"8kg sur les hanches, allongé au sol. Simule le hip thrust",                gif:"https://media.tenor.com/A5EMCkBEFvYAAAAd/hip-thrust-glutes.gif",          alts:["Pont fessier unilatéral","Hip thrust entre chaises"] },
    { name:"Fentes bulgares poids de corps",   et:"compound_secondary", loc:"home", f:"Grand Fessier - Amplitude",note:"Pied arrière sur chaise. Descente profonde = étirement max fessier",    gif:"https://media.tenor.com/xTxGJpnMLPcAAAAd/lunges-legs.gif",                alts:["Fentes marchées poids de corps","Pont fessier unilatéral"] },
    { name:"Donkey kicks",                     et:"isolation",          loc:"home", f:"Grand Fessier - Isolation",note:"A 4 pattes, pousser le talon vers le plafond. Sans matériel",            gif:"https://media.tenor.com/A5EMCkBEFvYAAAAd/hip-thrust-glutes.gif",          alts:["Pont fessier unilatéral","Abduction latérale au sol"] },
    { name:"Abduction latérale au sol",        et:"isolation",          loc:"home", f:"Moyen Fessier - Stabilité",note:"Allongé sur le côté, lever la jambe tendue. Progresser en reps",         gif:"https://media.tenor.com/A5EMCkBEFvYAAAAd/hip-thrust-glutes.gif",          alts:["Donkey kicks","Clamshell au sol"] },
  ],
  Mollets: [
    { name:"Mollets debout machine",           et:"isolation", loc:"gym",  f:"Gastrocnémien - Genou tendu", note:"Genou tendu = gastrocnémien en tension maximale. OBLIGATOIRE",             gif:"https://media.tenor.com/oDgqNnAjhJMAAAAd/calf-raises-calves.gif",         alts:["Mollets debout à la presse","Mollets unilatéral marche"] },
    { name:"Mollets assis machine",            et:"isolation", loc:"gym",  f:"Soléaire - Genou fléchi",     note:"Genou fléchi = soléaire seul actif. NON substituable par le debout",       gif:"https://media.tenor.com/oDgqNnAjhJMAAAAd/calf-raises-calves.gif",         alts:["Mollets assis haltère","Mollets assis chaise"] },
    { name:"Mollets debout à la presse",       et:"isolation", loc:"gym",  f:"Gastrocnémien - Genou tendu", note:"Alternative si pas de machine mollets debout. Même stimulus",              gif:"https://media.tenor.com/oDgqNnAjhJMAAAAd/calf-raises-calves.gif",         alts:["Mollets debout machine","Mollets unilatéral marche"] },
    { name:"Mollets unilatéral marche",        et:"isolation", loc:"home", f:"Gastrocnémien - Genou tendu", note:"Bord d'une marche, 1 pied à la fois. Amplitude maximale. Aucun matériel",  gif:"https://media.tenor.com/oDgqNnAjhJMAAAAd/calf-raises-calves.gif",         alts:["Mollets bilatéraux sol","Mollets assis chaise"] },
    { name:"Mollets assis chaise",             et:"isolation", loc:"home", f:"Soléaire - Genou fléchi",     note:"Assis sur chaise, genoux fléchis, 8kg sur les genoux. Soléaire seul",       gif:"https://media.tenor.com/oDgqNnAjhJMAAAAd/calf-raises-calves.gif",         alts:["Mollets assis machine","Mollets unilatéral marche"] },
  ],
  Abdominaux: [
    { name:"Ab wheel",                         et:"compound_secondary", loc:"gym",  f:"Grand Droit - Anti-ext", note:"Exercice le plus efficace : sangle entière sous tension",                  gif:"https://media.tenor.com/KBHdqPKJBkYAAAAd/crunches-abs.gif",               alts:["Crunch poulie haute","Relevé de jambes suspendu"] },
    { name:"Crunch poulie haute",              et:"isolation",          loc:"gym",  f:"Grand Droit - Flexion",  note:"Tension constante vs crunch sol. Résistance progressive",                 gif:"https://media.tenor.com/KBHdqPKJBkYAAAAd/crunches-abs.gif",               alts:["Ab wheel","Relevé de jambes suspendu"] },
    { name:"Relevé de jambes suspendu",        et:"compound_secondary", loc:"gym",  f:"Grand Droit - Force",    note:"Grand droit bas + fléchisseurs de hanche. Excellent exercice de force",   gif:"https://media.tenor.com/h9y8AAAAA_gAAAAd/leg-raises-abs.gif",             alts:["Crunch poulie haute","Ab wheel"] },
    { name:"Woodchopper poulie",               et:"isolation",          loc:"gym",  f:"Obliques - Rotation",    note:"Résistance constante sur tout l'arc de rotation. Supérieur au Russian twist", gif:"https://media.tenor.com/I_JFN0fGi-cAAAAd/plank-abs.gif",                alts:["Russian twist lesté","Gainage latéral"] },
    { name:"Relevé de jambes au sol",          et:"compound_secondary", loc:"home", f:"Grand Droit - Force",    note:"Allongé, jambes tendues à la verticale. Grand droit bas. Sans matériel",   gif:"https://media.tenor.com/h9y8AAAAA_gAAAAd/leg-raises-abs.gif",             alts:["Crunch vélo","Ab wheel maison"] },
    { name:"Ab wheel maison",                  et:"compound_secondary", loc:"home", f:"Grand Droit - Anti-ext", note:"Ab wheel environ 10 euros. Exercice le plus efficace des abdos",           gif:"https://media.tenor.com/KBHdqPKJBkYAAAAd/crunches-abs.gif",               alts:["Relevé de jambes au sol","Crunch vélo"] },
    { name:"Crunch vélo",                      et:"compound_secondary", loc:"home", f:"Obliques - Rotation",    note:"Coude vers genou opposé en pédalant. Obliques + grand droit",             gif:"https://media.tenor.com/KBHdqPKJBkYAAAAd/crunches-abs.gif",               alts:["Russian twist lesté","Relevé de jambes au sol"] },
    { name:"Russian twist lesté",              et:"isolation",          loc:"home", f:"Obliques - Rotation",    note:"Haltère 4-6kg. Rotation complète. Obliques sous tension constante",         gif:"https://media.tenor.com/I_JFN0fGi-cAAAAd/plank-abs.gif",                  alts:["Crunch vélo","Gainage latéral"] },
  ],
};

const CAT_FLAT = Object.keys(CATALOGUE).flatMap((m,mi) => CATALOGUE[m].map((e,i) => ({...e,muscle:m,id:mi*100+i})));
const MUSCLES  = Object.keys(CATALOGUE);
const MC = [
  {id:"pecs",    n:"Pectoraux",  e:"🫁"},
  {id:"dos",     n:"Dos",        e:"🦅"},
  {id:"epaules", n:"Épaules",    e:"🤷"},
  {id:"biceps",  n:"Biceps",     e:"💪"},
  {id:"triceps", n:"Triceps",    e:"🦾"},
  {id:"abdos",   n:"Abdominaux", e:"🏋️"},
  {id:"quadri",  n:"Quadriceps", e:"🦵"},
  {id:"fessiers",n:"Fessiers",   e:"🍑"},
  {id:"ischio",  n:"Ischio",     e:"🦿"},
  {id:"mollets", n:"Mollets",    e:"🦶"},
];
const MK = {pecs:"Pectoraux",dos:"Dos",epaules:"Épaules",biceps:"Biceps",triceps:"Triceps",
  abdos:"Abdominaux",quadri:"Quadriceps",fessiers:"Fessiers",ischio:"Ischio",mollets:"Mollets"};

const DPRIO = {
  homme:{dos:"high",epaules:"mid",pecs:"mid",triceps:"mid",quadri:"mid",ischio:"mid",biceps:"low",fessiers:"low",abdos:"low",mollets:"low"},
  femme:{fessiers:"high",ischio:"high",quadri:"mid",abdos:"mid",dos:"mid",epaules:"low",pecs:"low",triceps:"low",biceps:"low",mollets:"low"},
};

// ─── BUILDER ──────────────────────────────────────────────────────────────────
function buildProgram(prio, type, sets, days, split, gender, lieu) {
  const fem  = gender === "femme";
  const home = lieu   === "home";
  const RT2  = fem ? RTF : RT;
  const tN   = {force:"Force",hypertrophie:"Hypertrophie",endurance:"Endurance"}[type];
  const tM   = {force:.80,hypertrophie:1,endurance:1.15}[type];
  const dM   = {2:.55,3:.70,4:.85,5:1}[days]||1;
  const MIN=4, MAX=6;
  const ok   = e => home ? e.loc!=="gym" : e.loc!=="home";
  const vT   = {high:Math.round(15*tM*dM), mid:Math.round(10*tM*dM), low:Math.round(6*tM*dM)};

  const MAND = {
    gym: {
      dos:["Tractions pronation large","Rowing barre pronation","Extensions banc 45"],
      epaules:["Face pull poulie corde"], triceps:["Extension overhead poulie"],
      quadri:["Leg extension machine"],
      ischio:["SDT roumain barre","Leg curl assis machine"],
      mollets:["Mollets debout machine","Mollets assis machine"],
      biceps:["Curl incliné haltères","Curl marteau haltères"],
    },
    home:{
      dos:["Tractions prise large maison","Rowing haltère léger","Superman au sol"],
      epaules:["Oiseau haltères légers penché"], triceps:["Extension overhead haltère"],
      quadri:["Squat bulgare poids de corps","Fentes avant pied surélevé"],
      ischio:["SDT roumain haltères légers","Nordic curl"],
      mollets:["Mollets unilatéral marche","Mollets assis chaise"],
      biceps:["Curl haltères légers alterné","Curl marteau haltères légers"],
    },
  };

  function pool(mid) {
    const p = prio[mid]; if (!p) return [];
    const cat  = (CATALOGUE[MK[mid]]||[]).filter(ok);
    if (!cat.length) return [];
    const fais = [...new Set(cat.map(e=>e.f))];
    const mand = (MAND[home?"home":"gym"][mid]||[]).map(n=>cat.find(e=>e.name===n)).filter(Boolean);
    const nb   = Math.min(Math.max(Math.ceil(vT[p]/sets), fais.length, mand.length), cat.length);
    const sel  = [...mand];
    for (const e of cat) { if (sel.length>=nb) break; if (!sel.find(s=>s.name===e.name)) sel.push(e); }
    return sel.map(e=>({name:e.name,muscle:MK[mid],faisceau:e.f,exType:e.et,note:e.note,alts:e.alts,gif:e.gif,sets,reps:RT2[e.et]?.[type]||"8-12"}));
  }

  const P  = Object.fromEntries(MC.map(m=>[m.id,pool(m.id)]));
  const G  = id => P[id]||[];
  const sA = a  => { const s=new Set(); return a.filter(e=>!s.has(e.faisceau)&&s.add(e.faisceau)); };
  const sB = (a,ua) => { const u=new Set(ua.map(e=>e.name)); const m={}; a.forEach(e=>(m[e.faisceau]=m[e.faisceau]||[]).push(e)); return Object.values(m).map(x=>x.find(e=>!u.has(e.name))||x[0]); };

  const legs = max => {
    const raw = fem ? [...G("fessiers"),...G("ischio"),...G("quadri"),...G("mollets")]
                    : [...G("quadri"),...G("ischio"),...G("fessiers"),...G("mollets")];
    const c={};
    const res = raw.filter(e=>((c[e.faisceau]=(c[e.faisceau]||0)+1)<=2)).slice(0,max);
    // Garantir 1 exo rectus femoris (leg extension ou fentes surélevées) — toujours
    const rfExo = G("quadri").find(e=>e.faisceau.includes("ISO")||e.faisceau.includes("Rectus"));
    if (rfExo && !res.find(e=>e.name===rfExo.name) && res.length>=max) {
      res.pop(); res.splice(Math.min(2,res.length),0,rfExo);
    } else if (rfExo && !res.find(e=>e.name===rfExo.name)) {
      res.push(rfExo);
    }
    return res.slice(0,max);
  };

  const push = (p,e,t) => {
    const r=[...p.slice(0,2),...e.slice(0,2),...t.slice(0,1),...p.slice(2),...e.slice(2),...t.slice(1)];
    return r.filter((x,i,a)=>a.findIndex(y=>y.name===x.name)===i).slice(0,MAX);
  };

  const placeAbs = dl => {
    for (const ab of G("abs")) {
      const t=[...dl].filter(d=>d.exercises.length<MAX&&!d.exercises.some(e=>e.muscle==="Abdominaux")).sort((a,b)=>a.exercises.length-b.exercises.length)[0];
      if(t) t.exercises.push(ab);
    }
    return dl;
  };

  const eMin = dl => {
    const all = MC.flatMap(m=>G(m.id));
    for (const day of dl) {
      if (day.exercises.length>=MIN) continue;
      const uF=new Set(day.exercises.map(e=>e.faisceau)), uM=new Set(day.exercises.map(e=>e.muscle));
      for (const ex of all) {
        if (day.exercises.length>=MIN) break;
        if (!uF.has(ex.faisceau)&&!uM.has(ex.muscle)) { day.exercises.push(ex); uF.add(ex.faisceau); uM.add(ex.muscle); }
      }
    }
    return dl;
  };

  const fin = (dl, title) => { placeAbs(dl); eMin(dl); return {title, days:dl.filter(d=>d.exercises.length)}; };
  const SO  = ["Quadriceps","Ischio","Fessiers","Pectoraux","Dos","Épaules","Triceps","Biceps","Mollets","Abdominaux"];

  // FULL BODY
  if (split==="fullbody"||days<=2) {
    const ord = fem?["fessiers","ischio","quadri","pecs","dos","epaules","triceps","biceps"]:["quadri","ischio","fessiers","pecs","dos","epaules","triceps","biceps"];
    const bk  = Array.from({length:days},()=>[]);
    ord.forEach(id=>G(id).forEach((e,i)=>bk[i%days].push(e)));
    return fin(bk.map((ex,i)=>({name:`Jour ${i+1} — Full Body`,focus:"Corps entier",exercises:[...ex].sort((a,b)=>SO.indexOf(a.muscle)-SO.indexOf(b.muscle))})),`${tN} · Full Body · ${days}j/sem`);
  }

  // PPL
  if (split==="ppl") {
    const fixPB = (d,a) => {
      const b=[...d]; if(b.length>=MIN) return b.slice(0,MAX);
      const u=new Set(a.map(e=>e.name)), ex=[...G("dos"),...G("biceps")].filter(e=>!u.has(e.name)), r=[...b]; const sf=new Set(r.map(e=>e.faisceau));
      for(const e of ex){if(r.length>=MIN)break;if(!sf.has(e.faisceau)){r.push(e);sf.add(e.faisceau);}}
      for(const e of [...G("dos"),...G("biceps")]){if(r.length>=MIN)break;if(!r.find(x=>x.name===e.name))r.push(e);}
      return r.slice(0,MAX);
    };
    if (days===3) {
      return fin([
        {name:"Jour 1 — Push", focus:"Pectoraux · Épaules · Triceps",        exercises:push(G("pecs"),G("epaules"),G("triceps"))},
        {name:"Jour 2 — Pull", focus:"Dos · Biceps",                         exercises:[...G("dos"),...G("biceps")].slice(0,MAX)},
        {name:"Jour 3 — Legs", focus:"Quadriceps · Fessiers · Ischio",       exercises:legs(MAX)},
      ],`${tN} · PPL · 3j/sem`);
    }
    if (days===4) {
      const pa=[...G("dos"),...G("biceps")].slice(0,MAX);
      const up=()=>{const r=[],s=new Set();for(const e of[...G("pecs"),...G("dos"),...G("epaules"),...G("triceps"),...G("biceps")]){if(r.length>=MAX)break;if(!s.has(e.faisceau)){r.push(e);s.add(e.faisceau);}}return r;};
      return fin([
        {name:"Jour 1 — Push",  focus:"Pectoraux · Épaules · Triceps",  exercises:push(G("pecs"),G("epaules"),G("triceps"))},
        {name:"Jour 2 — Pull",  focus:"Dos · Biceps",                   exercises:pa},
        {name:"Jour 3 — Legs",  focus:"Quadriceps · Fessiers · Ischio", exercises:legs(MAX)},
        {name:"Jour 4 — Upper", focus:"Haut du corps",                  exercises:up()},
      ],`${tN} · PPL · 4j/sem`);
    }
    const pAp=sA(G("pecs")), pBp=sB(G("pecs"),pAp);
    const pAe=sA(G("epaules")), pBe=sB(G("epaules"),pAe);
    const pAt=sA(G("triceps")), pBt=sB(G("triceps"),pAt);
    const pAd=sA(G("dos")), pBd=sB(G("dos"),pAd);
    const pAb=sA(G("biceps")), pBb=sB(G("biceps"),pAb);
    const pa5=[...pAd,...pAb].slice(0,MAX);
    return fin([
      {name:"Jour 1 — Push A", focus:"Pecs composé · Épaules · Triceps overhead", exercises:push(pAp,pAe,pAt)},
      {name:"Jour 2 — Pull A", focus:"Dos vertical horizontal · Biceps",           exercises:pa5},
      {name:"Jour 3 — Legs",   focus:"Quadriceps · Fessiers · Ischio",             exercises:legs(MAX)},
      {name:"Jour 4 — Push B", focus:"Pecs iso · Épaules iso · Triceps latéral",   exercises:push(pBp,pBe,pBt)},
      {name:"Jour 5 — Pull B", focus:"Dos iso · Biceps chef court brachial",       exercises:fixPB([...pBd,...pBb],pa5)},
    ],`${tN} · PPL · 5j/sem`);
  }

  // BRO
  const itl = (a,b) => {const r=[],m=Math.max(a.length,b.length);for(let i=0;i<m;i++){if(a[i])r.push(a[i]);if(b[i])r.push(b[i]);}return r;};
  const bP  = ()=>{const r=[],s=new Set();for(const e of[...G("pecs"),...G("triceps")]){if(r.length>=MAX)break;if(!s.has(e.f)){r.push(e);s.add(e.f);}}for(const e of[...G("pecs"),...G("triceps")]){if(r.length>=MAX)break;if(!r.find(x=>x.name===e.name))r.push(e);}return r.slice(0,MAX);};
  const bE  = ()=>{const r=[...G("epaules")];if(r.length<MIN){const s=new Set(r.map(e=>e.muscle));for(const e of[...G("triceps"),...G("biceps")]){if(r.length>=MIN)break;if(!s.has(e.muscle)){r.push(e);s.add(e.muscle);}}}return r.slice(0,MAX);};
  const sl  = [{l:"Pectoraux",f:"Pectoraux · Triceps",e:bP()},{l:"Dos",f:"Dos · Biceps",e:[...G("dos"),...G("biceps")].slice(0,MAX)},{l:"Épaules",f:"Épaules",e:bE()},{l:"Bras",f:"Biceps · Triceps",e:itl(G("triceps"),G("biceps")).slice(0,MAX)},{l:"Jambes",f:"Quadriceps · Fessiers · Ischio",e:legs(MAX)}].filter(s=>s.e.length);
  return fin(Array.from({length:days},(_,i)=>{const s=sl[i%sl.length];return{name:`Jour ${i+1} — ${s.l}`,focus:s.f,exercises:[...s.e]};}),`${tN} · Bro Split · ${days}j/sem`);
}

// ─── THEME ────────────────────────────────────────────────────────────────────
const C={bg:"#0e0e0f",s:"#18181b",s2:"#222226",bd:"#2e2e33",ac:"#e8ff47",tx:"#f0f0f0",mu:"#7a7a85",lo:"#3b82f6",mi:"#f59e0b",hi:"#ef4444",ok:"#22c55e"};
const chip=on=>({flex:1,minWidth:70,padding:"12px 8px",background:on?"rgba(232,255,71,.07)":C.s2,border:`2px solid ${on?C.ac:C.bd}`,borderRadius:9,textAlign:"center",cursor:"pointer"});
const pill=(on,lv)=>({flex:1,padding:"5px 0",border:"none",borderRadius:5,fontSize:10,fontWeight:700,cursor:"pointer",background:on?(lv==="low"?C.lo:lv==="mid"?C.mi:C.hi):C.bd,color:on?(lv==="mid"?"#000":"#fff"):C.mu});
const fmt=d=>new Date(d).toLocaleDateString("fr-FR",{day:"2-digit",month:"2-digit"});
const ago=ts=>Math.floor((Date.now()-ts)/86400000);
const gif=name=>CAT_FLAT.find(e=>e.name===name)?.gif||null;
const alts=name=>CAT_FLAT.find(e=>e.name===name)?.alts||[];

// ─── MINI CHART ───────────────────────────────────────────────────────────────
function MiniChart({pts}){
  if(!pts||pts.length<2) return null;
  const v=pts.map(p=>p.v),mn=Math.min(...v),mx=Math.max(...v),rng=mx-mn||1;
  const W=220,H=56,pd=6,x=i=>pd+(i/(pts.length-1))*(W-pd*2),y=val=>H-pd-((val-mn)/rng)*(H-pd*2);
  return <svg width="100%" viewBox={`0 0 ${W} ${H+14}`} style={{overflow:"visible"}}>
    <path d={pts.map((p,i)=>`${i?"L":"M"}${x(i).toFixed(1)},${y(p.v).toFixed(1)}`).join(" ")} fill="none" stroke={C.ac} strokeWidth="2" strokeLinecap="round"/>
    {pts.map((p,i)=><g key={i}><circle cx={x(i)} cy={y(p.v)} r="3" fill={C.ac}/><text x={x(i)} y={y(p.v)-7} textAnchor="middle" fill={C.ac} fontSize="9" fontWeight="700">{p.v}kg</text><text x={x(i)} y={H+12} textAnchor="middle" fill={C.mu} fontSize="8">{fmt(p.ts)}</text></g>)}
  </svg>;
}

// ─── SWAP MODAL ───────────────────────────────────────────────────────────────
function SwapModal({ex,onSwap,onClose}){
  const list=alts(ex.name);
  return <div style={{position:"fixed",inset:0,background:"rgba(0,0,0,.85)",zIndex:100,display:"flex",alignItems:"flex-end"}} onClick={onClose}>
    <div style={{background:C.s,borderRadius:"16px 16px 0 0",padding:"20px 16px 32px",width:"100%",maxWidth:680,margin:"0 auto"}} onClick={e=>e.stopPropagation()}>
      <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:14}}>
        <div><div style={{fontWeight:700,fontSize:15}}>Changer l&apos;exercice</div><div style={{fontSize:11,color:C.mu,marginTop:2}}>{ex.name}</div></div>
        <button onClick={onClose} style={{background:C.s2,border:"none",color:C.mu,borderRadius:8,padding:"6px 12px",fontSize:13,fontWeight:700,cursor:"pointer"}}>✕</button>
      </div>
      {!list.length
        ? <div style={{color:C.mu,fontSize:13,textAlign:"center",padding:"20px 0"}}>Pas d&apos;alternatives disponibles.</div>
        : list.map((n,i)=>{const alt=CAT_FLAT.find(e=>e.name===n); return <div key={i} style={{background:C.s2,border:`1px solid ${C.bd}`,borderRadius:10,marginBottom:10}}>
            <div style={{padding:"12px 14px",display:"flex",justifyContent:"space-between",alignItems:"flex-start",gap:10}}>
              <div style={{flex:1}}><div style={{fontWeight:700,fontSize:13,marginBottom:3}}>{n}</div>{alt?.note&&<div style={{fontSize:11,color:C.mu,lineHeight:1.5}}>{alt.note}</div>}</div>
              <button onClick={()=>onSwap(n)} style={{padding:"8px 14px",borderRadius:8,border:"none",fontWeight:700,fontSize:12,background:C.ac,color:"#000",flexShrink:0,cursor:"pointer"}}>Choisir</button>
            </div>
          </div>;})
      }
    </div>

    
  </div>;
}

// ─── EXO CARD ─────────────────────────────────────────────────────────────────
function ExoCard({ex,onAdd,added}){
  const [sg,setSg]=useState(false);
  const g=ex.gif||gif(ex.name);
  return <div style={{background:C.s2,border:`1px solid ${added?C.ac:C.bd}`,borderRadius:10,overflow:"hidden"}}>
    <div style={{position:"relative",height:110,background:"#111",cursor:g?"pointer":"default"}} onClick={()=>g&&setSg(v=>!v)}>
      {sg&&g?<img src={g} alt={ex.name} style={{width:"100%",height:"100%",objectFit:"cover"}}/>
      :<div style={{width:"100%",height:"100%",display:"flex",alignItems:"center",justifyContent:"center",flexDirection:"column",gap:4}}><div style={{fontSize:26}}>💪</div>{g&&<div style={{fontSize:9,color:C.mu}}>Tap GIF</div>}</div>}
      {g&&<div style={{position:"absolute",bottom:4,right:5,background:"rgba(0,0,0,.8)",color:C.ac,fontSize:9,padding:"2px 6px",borderRadius:8,fontWeight:700}}>{sg?"■":"▶"}</div>}
    </div>
    <div style={{padding:"9px 10px"}}>
      <div style={{fontWeight:600,fontSize:12,marginBottom:1}}>{ex.name}</div>
      {ex.f&&<div style={{fontSize:9,color:C.ac,marginBottom:2,fontWeight:700,textTransform:"uppercase",letterSpacing:.5}}>{ex.f}</div>}
      <div style={{fontSize:10,color:C.mu,marginBottom:ex.note?4:7}}>{ex.muscle}</div>
      {ex.note&&<div style={{fontSize:10,color:"#7a7a95",marginBottom:7,lineHeight:1.4,fontStyle:"italic"}}>{ex.note}</div>}
      <button onClick={()=>onAdd(ex)} style={{width:"100%",padding:"5px 0",border:"none",borderRadius:6,fontWeight:700,fontSize:11,cursor:"pointer",background:added?C.s:C.ac,color:added?C.mu:"#000"}}>{added?"✓ Ajouté":"+ Ajouter"}</button>
    </div>
  </div>;
}

// ─── PROGRAM CARD ─────────────────────────────────────────────────────────────
function ProgramCard({prog,onLaunch,onDelete}){
  const [open,setOpen]=useState(false);
  return <div style={{background:C.s,border:`1px solid ${C.bd}`,borderRadius:12,marginBottom:10,overflow:"hidden"}}>
    <div style={{padding:"14px 16px",display:"flex",justifyContent:"space-between",alignItems:"center"}}>
      <div style={{flex:1,cursor:"pointer",minWidth:0}} onClick={()=>setOpen(o=>!o)}>
        <div style={{fontWeight:700,fontSize:15,overflow:"hidden",textOverflow:"ellipsis",whiteSpace:"nowrap"}}>{prog.title}</div>
        <div style={{fontSize:11,color:C.mu,marginTop:2}}>{prog.days.length} jours · {prog.days.reduce((a,d)=>a+d.exercises.length,0)} exercices</div>
        <div style={{fontSize:10,color:C.mu,marginTop:3}}>{open?"▲ Masquer":"▼ Voir"}</div>
      </div>
      <div style={{display:"flex",flexDirection:"column",gap:6,marginLeft:12,flexShrink:0}}>
        <button onClick={()=>onLaunch(prog)} style={{padding:"8px 16px",borderRadius:8,border:"none",fontWeight:700,fontSize:12,cursor:"pointer",background:C.ac,color:"#000"}}>▶ Lancer</button>
        <button onClick={()=>onDelete(prog.id)} style={{padding:"6px 12px",borderRadius:8,border:"1px solid rgba(239,68,68,.3)",fontWeight:600,fontSize:11,cursor:"pointer",background:"rgba(239,68,68,.1)",color:C.hi}}>Supprimer</button>
      </div>
    </div>
    {open&&<div style={{borderTop:`1px solid ${C.bd}`,padding:"0 16px 14px"}}>
      {prog.days.map((d,di)=><div key={di} style={{marginTop:10}}>
        <div style={{fontWeight:700,fontSize:12,color:C.ac,marginBottom:5}}>{d.name}</div>
        {d.exercises.map((ex,ei)=><div key={ei} style={{fontSize:12,padding:"4px 0",borderBottom:`1px solid ${C.bd}`,display:"flex",justifyContent:"space-between"}}><span>{ex.name}</span><span style={{color:C.mu}}>{ex.sets}× {ex.reps}</span></div>)}
      </div>)}
    </div>}
  </div>;
}

// ─── SESSION TRACKER ──────────────────────────────────────────────────────────
function SessionTracker({program,history,onSave}){
  const [di,setDi]=useState(0),[logs,setL]=useState({}),[done,setD]=useState({}),[gi,setGi]=useState(null),[sw,setSw]=useState(null),[ov,setOv]=useState({}),[saved,setSaved]=useState(false);
  const day=program.days[di], exos=ov[di]||day.exercises;
  const tot=exos.reduce((a,e)=>a+(e.sets||3),0), dn=Object.values(done).filter(Boolean).length, pct=Math.round(dn/tot*100)||0;
  const h2w=n=>{
    // Retourne les 2 dernières séances où cet exercice a été fait (avec tous les sets)
    const sessions=(history||[])
      .filter(s=>s.exercises?.some(x=>x.name===n))
      .sort((a,b)=>b.ts-a.ts)
      .slice(0,2);
    return sessions.map(s=>({ts:s.ts,sets:s.exercises.find(x=>x.name===n)?.sets||[]}));
  };
  const swap=(ei,n)=>{const nx=[...exos],d=CAT_FLAT.find(e=>e.name===n);nx[ei]={...nx[ei],name:n,muscle:d?.muscle||nx[ei].muscle,note:d?.note,alts:d?.alts||[]};setOv(p=>({...p,[di]:nx}));setD(d2=>{const nd={...d2};for(let si=0;si<(nx[ei].sets||3);si++)delete nd[`${ei}-${si}`];return nd;});setL(l=>{const nl={...l};Object.keys(nl).forEach(k=>{if(k.startsWith(`${ei}-`))delete nl[k];});return nl;});setSw(null);};
  const save=()=>{onSave({ts:Date.now(),programTitle:program.title,dayName:day.name,exercises:exos.map((ex,ei)=>({name:ex.name,muscle:ex.muscle,sets:Array.from({length:ex.sets||3},(_,si)=>({reps:logs[`${ei}-${si}-r`]||"",kg:logs[`${ei}-${si}-k`]||"",done:!!done[`${ei}-${si}`]}))}))});setSaved(true);};
  const inp=d=>({background:d?"#111":C.s2,border:`1px solid ${C.bd}`,borderRadius:6,padding:"7px",color:d?C.mu:C.tx,textAlign:"center",fontSize:13,width:"100%"});
  return <div>
    {sw&&<SwapModal ex={sw.ex} onSwap={n=>swap(sw.ei,n)} onClose={()=>setSw(null)}/>}
    <div style={{background:C.s,border:`1px solid ${C.bd}`,borderRadius:10,padding:"12px 14px",marginBottom:12}}>
      <div style={{display:"flex",justifyContent:"space-between",marginBottom:5}}><span style={{fontSize:12,color:C.mu}}>{program.title}</span><span style={{fontWeight:800,fontSize:14,color:pct===100?C.ok:C.ac}}>{pct}%</span></div>
      <div style={{background:C.bd,borderRadius:8,height:5,overflow:"hidden"}}><div style={{width:pct+"%",height:"100%",background:pct===100?C.ok:C.ac,transition:"width .3s"}}/></div>
    </div>
    <div style={{display:"flex",gap:5,marginBottom:12}}>
      {program.days.map((d,i)=><button key={i} onClick={()=>{setDi(i);setD({});setL({});setSaved(false);}} style={{padding:"6px 13px",borderRadius:8,border:`2px solid ${i===di?C.ac:C.bd}`,background:i===di?"rgba(232,255,71,.1)":C.s2,color:i===di?C.ac:C.mu,fontWeight:700,fontSize:11,cursor:"pointer"}}>J{i+1}</button>)}
    </div>
    <div style={{fontWeight:700,fontSize:15,marginBottom:1}}>{day.name}</div>
    <div style={{fontSize:11,color:C.mu,marginBottom:12}}>{day.focus}</div>
    {exos.map((ex,ei)=>{
      const s=ex.sets||3, ed=Array.from({length:s},(_,si)=>done[`${ei}-${si}`]).filter(Boolean).length, g=ex.gif||gif(ex.name), h=h2w(ex.name);
      return <div key={ei} style={{background:C.s,border:`1px solid ${C.bd}`,borderRadius:10,marginBottom:10,overflow:"hidden"}}>
        <div style={{padding:"10px 13px",background:C.s2,borderBottom:`1px solid ${C.bd}`}}>
          <div style={{display:"flex",justifyContent:"space-between",alignItems:"flex-start"}}>
            <div style={{flex:1}}>
              <div style={{fontWeight:700,fontSize:14}}>{ex.name}</div>
              {ex.faisceau&&<div style={{fontSize:9,color:C.ac,fontWeight:700,textTransform:"uppercase",letterSpacing:.5,marginTop:1}}>{ex.faisceau}</div>}
              <div style={{fontSize:11,color:C.mu,marginTop:1}}>{ex.muscle} · {ex.reps||"8-12"} reps</div>
              {ex.note&&<div style={{fontSize:10,color:"#6a6a80",marginTop:3,lineHeight:1.4,fontStyle:"italic"}}>{ex.note}</div>}
            </div>
            <div style={{display:"flex",gap:6,alignItems:"center",marginLeft:8,flexShrink:0}}>
              <div style={{fontWeight:800,fontSize:18,color:ed===s?C.ok:C.ac}}>{ed}/{s}</div>
              {g&&<button onClick={()=>setGi(gi===ei?null:ei)} style={{background:C.bd,border:"none",color:C.ac,borderRadius:6,padding:"4px 8px",cursor:"pointer",fontSize:11,fontWeight:700}}>{gi===ei?"✕":"▶"}</button>}
            </div>
          </div>
          <button onClick={()=>setSw({ei,ex})} style={{marginTop:8,padding:"5px 12px",borderRadius:7,border:`1px solid ${C.bd}`,background:"transparent",color:C.mu,fontSize:11,fontWeight:600,cursor:"pointer"}}>🔄 Changer {(ex.alts||[]).length>0?`(${(ex.alts||[]).length} alt.)`:""}</button>
        </div>
        {gi===ei&&g&&<div style={{background:"#111",textAlign:"center",padding:8}}><img src={g} alt={ex.name} style={{maxHeight:160,maxWidth:"100%",borderRadius:8}} onError={e=>{e.target.style.display="none"}}/></div>}
        {h.length>0&&<div style={{padding:"8px 13px",borderBottom:`1px solid ${C.bd}`,background:"rgba(232,255,71,.03)"}}>
          <div style={{display:"flex",gap:8}}>
            {h.map((sess,hi)=>(
              <div key={hi} style={{flex:1}}>
                <div style={{fontSize:9,color:C.ac,textTransform:"uppercase",letterSpacing:1,fontWeight:700,marginBottom:5}}>{fmt(sess.ts)}</div>
                {sess.sets.filter(s=>s.done&&s.reps).map((s,si)=>(
                  <div key={si} style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:3}}>
                    <span style={{fontSize:9,color:C.mu,minWidth:14}}>{si+1}</span>
                    <span style={{fontSize:12,fontWeight:700,color:C.tx}}>{s.reps}<span style={{fontSize:9,color:C.mu,fontWeight:400}}>reps</span></span>
                    <span style={{fontSize:12,fontWeight:700,color:s.kg?C.ac:C.mu}}>{s.kg?s.kg+"kg":"—"}</span>
                  </div>
                ))}
                {!sess.sets.filter(s=>s.done&&s.reps).length&&(
                  <div style={{fontSize:10,color:C.mu,fontStyle:"italic"}}>—</div>
                )}
              </div>
            ))}
          </div>
        </div>}
        <div style={{padding:"8px 13px"}}>
          <div style={{display:"grid",gridTemplateColumns:"28px 1fr 1fr 34px",gap:6,marginBottom:4}}>{["#","Reps","kg",""].map((h,i)=><div key={i} style={{fontSize:10,color:C.mu,textAlign:"center"}}>{h}</div>)}</div>
          {Array.from({length:s},(_,si)=>{const k=`${ei}-${si}`,d2=!!done[k];return <div key={si} style={{display:"grid",gridTemplateColumns:"28px 1fr 1fr 34px",gap:6,marginBottom:5,alignItems:"center"}}>
            <div style={{textAlign:"center",fontWeight:800,fontSize:16,color:C.ac}}>{si+1}</div>
            <input type="number" placeholder={ex.reps?.split("-")[0]||"8"} disabled={d2} value={logs[`${ei}-${si}-r`]||""} onChange={e=>setL(l=>({...l,[`${ei}-${si}-r`]:e.target.value}))} style={inp(d2)}/>
            <input type="number" placeholder="kg" disabled={d2} value={logs[`${ei}-${si}-k`]||""} onChange={e=>setL(l=>({...l,[`${ei}-${si}-k`]:e.target.value}))} style={inp(d2)}/>
            <button onClick={()=>setD(d3=>({...d3,[k]:!d3[k]}))} style={{width:32,height:32,borderRadius:6,border:`2px solid ${d2?C.ok:C.bd}`,background:d2?C.ok:"transparent",color:d2?"#000":C.mu,cursor:"pointer",fontSize:14,display:"flex",alignItems:"center",justifyContent:"center"}}>{d2?"✓":"○"}</button>
          </div>;})}
        </div>
      </div>;
    })}
    
    {pct===100&&<div style={{background:"rgba(34,197,94,.1)",border:`1px solid ${C.ok}`,borderRadius:10,padding:"16px",textAlign:"center",marginTop:4,marginBottom:10}}><div style={{fontSize:28,marginBottom:4}}>🏆</div><div style={{fontWeight:700,fontSize:16,color:C.ok}}>Séance terminée !</div></div>}
    <button onClick={save} disabled={saved} style={{width:"100%",padding:14,borderRadius:10,border:"none",fontWeight:800,fontSize:15,cursor:saved?"default":"pointer",background:saved?C.s2:C.ok,color:saved?C.mu:"#000",marginTop:4}}>{saved?"✓ Séance sauvegardée !":"💾 Sauvegarder la séance"}</button>
  </div>;
}

// ─── STATS ────────────────────────────────────────────────────────────────────
function StatsPage({history}){
  const [sel,setSel]=useState(null);
  if(!history?.length) return <div style={{textAlign:"center",padding:"60px 20px"}}><div style={{fontSize:44,marginBottom:12}}>📊</div><div style={{fontWeight:700,fontSize:17,marginBottom:6}}>Aucune donnée</div><div style={{color:C.mu,fontSize:13}}>Complète des séances pour voir ta progression</div></div>;
  const map={};
  history.forEach(s=>s.exercises?.forEach(ex=>{if(!map[ex.name])map[ex.name]={name:ex.name,muscle:ex.muscle,pts:[]};const b=ex.sets?.filter(s=>s.kg&&s.done).sort((a,bb)=>parseFloat(bb.kg)-parseFloat(a.kg))[0];if(b)map[ex.name].pts.push({ts:s.ts,v:parseFloat(b.kg),reps:b.reps});}));
  const exos=Object.values(map).filter(e=>e.pts.length), sd=sel?map[sel]:null;
  const tot=history.reduce((a,s)=>a+(s.exercises?.reduce((b,e)=>b+(e.sets?.filter(x=>x.done).length||0),0)||0),0);
  return <div>
    <div style={{display:"grid",gridTemplateColumns:"repeat(3,1fr)",gap:8,marginBottom:18}}>
      {[[history.length,"Séances"],[tot,"Séries"],[history.filter(s=>ago(s.ts)<7).length,"Cette sem."]].map(([v,l],i)=><div key={i} style={{background:C.s2,borderRadius:10,padding:"12px 8px",textAlign:"center"}}><div style={{fontWeight:800,fontSize:28,color:C.ac}}>{v}</div><div style={{fontSize:10,color:C.mu}}>{l}</div></div>)}
    </div>
    <div style={{fontSize:10,textTransform:"uppercase",letterSpacing:2,color:C.mu,marginBottom:10}}>Progression par exercice</div>
    <div style={{display:"flex",gap:5,marginBottom:14}}>{exos.map(e=><button key={e.name} onClick={()=>setSel(sel===e.name?null:e.name)} style={{padding:"5px 11px",borderRadius:18,border:`1px solid ${sel===e.name?C.ac:C.bd}`,background:sel===e.name?"rgba(232,255,71,.1)":"transparent",color:sel===e.name?C.ac:C.mu,fontSize:11,fontWeight:600,cursor:"pointer"}}>{e.name}</button>)}</div>
    {sd&&<div style={{background:C.s,border:`1px solid ${C.bd}`,borderRadius:12,padding:"16px",marginBottom:14}}>
      <div style={{fontWeight:700,fontSize:14,marginBottom:1}}>{sd.name}</div>
      <div style={{fontSize:11,color:C.mu,marginBottom:12}}>{sd.muscle}</div>
      {sd.pts.length>=2?<MiniChart pts={sd.pts}/>:<div style={{color:C.mu,fontSize:12}}>2 séances min pour la courbe</div>}
      <div style={{marginTop:14}}>{sd.pts.slice().reverse().map((p,i,a)=>{const pr=a[i+1],df=pr?+(p.v-pr.v).toFixed(1):null;return <div key={i} style={{display:"flex",justifyContent:"space-between",padding:"7px 0",borderBottom:`1px solid ${C.bd}`}}><span style={{color:C.mu,fontSize:12}}>{fmt(p.ts)}</span><span style={{fontWeight:700,fontSize:13}}>{p.v}kg × {p.reps}</span>{df!==null&&<span style={{fontSize:11,color:df>0?C.ok:df<0?C.hi:C.mu,fontWeight:700}}>{df>0?"+":""}{df}kg</span>}</div>;})}</div>
    </div>}
    <div style={{fontSize:10,textTransform:"uppercase",letterSpacing:2,color:C.mu,marginBottom:10}}>Historique</div>
    {history.slice().reverse().map((s,i)=><div key={i} style={{background:C.s,border:`1px solid ${C.bd}`,borderRadius:10,padding:"12px 14px",marginBottom:8}}>
      <div style={{display:"flex",justifyContent:"space-between",marginBottom:4}}><div style={{fontWeight:700,fontSize:13}}>{s.dayName}</div><div style={{fontSize:11,color:C.mu}}>{fmt(s.ts)}</div></div>
      <div style={{fontSize:11,color:C.mu,marginBottom:6}}>{s.programTitle}</div>
      <div style={{display:"flex",gap:5}}>{s.exercises?.map((ex,j)=>{const b=ex.sets?.filter(x=>x.kg&&x.done).sort((a,bb)=>parseFloat(bb.kg)-parseFloat(a.kg))[0];return b&&<span key={j} style={{background:C.s2,border:`1px solid ${C.bd}`,borderRadius:14,padding:"3px 9px",fontSize:11}}>{ex.name} · <strong>{b.kg}kg</strong></span>;})}</div>
    </div>)}
  </div>;
}

// ─── APP ──────────────────────────────────────────────────────────────────────
export default function App(){
  const [tab,setTab]=useState("programs");
  // ── Chronomètre (stopwatch — 3 états : stop@0 → run → stop@X → reset) ──
  const [tSec,setTSec]=useState(0),[tRun,setTRun]=useState(false);
  const tRef=useRef(null);
  useEffect(()=>{
    if(tRun){tRef.current=setInterval(()=>setTSec(s=>s+1),1000);}
    else{clearInterval(tRef.current);}
    return()=>clearInterval(tRef.current);
  },[tRun]);
  const tapTimer=()=>{
    if(!tRun&&tSec===0){setTRun(true);}        // état 0 → démarrer
    else if(tRun){setTRun(false);}              // état 1 → arrêter
    else{setTSec(0);}                           // état 2 → remettre à 0
  };
  const fmt2=s=>`${String(Math.floor(s/60)).padStart(2,"0")}:${String(s%60).padStart(2,"0")}`;
  const [progs,setProgs]=useStorage("im_programs",[]);
  const [hist,setHist]=useStorage("im_history",[]);
  const [activeP,setActiveP]=useState(null);
  const [phase,setPhase]=useState(0);
  const [gender,setGender]=useState(null);
  const [lieu,setLieu]=useState(null);
  const [prio,setPrio]=useState({});
  const [type,setType]=useState("hypertrophie");
  const [sets,setSets]=useState(3);
  const [days,setDays]=useState(3);
  const [split,setSplit]=useState("ppl");
  const [pName,setPName]=useState("");
  const [gen,setGen]=useState(null);
  const [fM,setFM]=useState("Tous");
  const [fLoc,setFLoc]=useState("gym");
  const [srch,setSrch]=useState("");
  const [cDays,setCDays]=useState([{name:"Jour 1",exercises:[]}]);
  const [cDay,setCDay]=useState(0);
  const [cName,setCName]=useState("");

  const tP=(id,lv)=>setPrio(p=>({...p,[id]:p[id]===lv?undefined:lv}));
  const go1=()=>{if(!gender||!lieu)return;setPrio(DPRIO[gender]||{});setPhase(1);};

  const doGen=()=>{const p=buildProgram(prio,type,sets,days,split,gender,lieu);if(!p.days?.length){alert("Sélectionne au moins un groupe musculaire.");return;}p.id=Date.now();p.title=pName||p.title;setGen(p);};
  const saveG=()=>{if(!gen)return;setProgs(p=>[...p,gen]);setGen(null);setPName("");setPhase(0);setGender(null);setLieu(null);setTab("programs");};
  const addCD=()=>{setCDays(d=>[...d,{name:`Jour ${d.length+1}`,exercises:[]}]);setCDay(cDays.length);};
  const remCD=i=>{if(cDays.length<=1)return;const nd=cDays.filter((_,x)=>x!==i);setCDays(nd);setCDay(Math.max(0,Math.min(cDay,nd.length-1)));};
  const addEx=ex=>{if(cDays[cDay].exercises.find(e=>e.name===ex.name))return;setCDays(d=>d.map((day,i)=>i===cDay?{...day,exercises:[...day.exercises,{name:ex.name,muscle:ex.muscle,faisceau:ex.f,exType:ex.et,note:ex.note,gif:ex.gif,alts:ex.alts,sets,reps:RT[ex.et]?.hypertrophie||"8-12"}]}:day));};
  const remEx=ei=>setCDays(d=>d.map((day,i)=>i===cDay?{...day,exercises:day.exercises.filter((_,x)=>x!==ei)}:day));
  const savC=()=>{if(!cName.trim()){alert("Donne un nom à ton programme");return;}setProgs(p=>[...p,{id:Date.now(),title:cName,days:cDays.filter(d=>d.exercises.length)}]);setCDays([{name:"Jour 1",exercises:[]}]);setCName("");setCDay(0);setTab("programs");};

  const filtered=CAT_FLAT.filter(e=>(fM==="Tous"||e.muscle===fM)&&(e.loc===fLoc||e.loc==="both")&&(!srch||e.name.toLowerCase().includes(srch.toLowerCase())));
  const cEN=cDays[cDay]?.exercises.map(e=>e.name)||[];
  const NAV=[["programs","Programmes","📋"],["generate","Générer","⚡"],["custom","Créer","🛠️"],["session","Séance","💪"],["stats","Suivi","📊"]];
  const PRIOS=[["low","Faible","rgba(59,130,246,.15)"],["mid","Moyen","rgba(245,158,11,.15)"],["high","Import.","rgba(239,68,68,.15)"]];

  return <div style={{background:C.bg,color:C.tx,fontFamily:"system-ui,sans-serif",minHeight:"100vh",maxWidth:680,margin:"0 auto",display:"flex",flexDirection:"column"}}>
    <style>{`*{box-sizing:border-box}input{outline:none;font-family:inherit}input:focus{border-color:#e8ff47!important}button{font-family:inherit;cursor:pointer}`}</style>

    {/* NAV */}
    <div style={{padding:"14px 16px 0",borderBottom:`1px solid ${C.bd}`,background:C.bg,position:"sticky",top:0,zIndex:10}}>
      <div style={{fontWeight:900,fontSize:24,color:C.ac,letterSpacing:3,marginBottom:10}}>IRONMIND</div>
      <div style={{display:"flex"}}>
        {NAV.map(([id,label,emoji])=><button key={id} onClick={()=>setTab(id)} style={{flex:1,padding:"8px 2px",border:"none",borderBottom:`3px solid ${tab===id?C.ac:"transparent"}`,background:"transparent",color:tab===id?C.ac:C.mu,fontWeight:700,fontSize:10,display:"flex",flexDirection:"column",alignItems:"center",gap:2}}><span style={{fontSize:16}}>{emoji}</span>{label}</button>)}
      </div>
    </div>

    <div style={{flex:1,overflowY:"auto",padding:"20px 16px 40px"}}>

      {/* PROGRAMMES */}
      {tab==="programs"&&<div>
        <div style={{fontWeight:700,fontSize:18,marginBottom:4}}>Mes programmes</div>
        <div style={{color:C.mu,fontSize:12,marginBottom:16}}>Appuie sur ▶ Lancer pour démarrer une séance</div>
        {!progs.length
          ?<div style={{background:C.s,border:`1px solid ${C.bd}`,borderRadius:12,padding:"32px 20px",textAlign:"center"}}>
            <div style={{fontSize:36,marginBottom:10}}>📋</div>
            <div style={{fontWeight:600,fontSize:15,marginBottom:6}}>Aucun programme sauvegardé</div>
            <div style={{color:C.mu,fontSize:12,marginBottom:16}}>Génère ou crée ton premier programme</div>
            <div style={{display:"flex",gap:8,justifyContent:"center"}}>
              <button onClick={()=>setTab("generate")} style={{padding:"9px 18px",borderRadius:8,border:"none",fontWeight:700,fontSize:13,background:C.ac,color:"#000"}}>⚡ Générer</button>
              <button onClick={()=>setTab("custom")}   style={{padding:"9px 18px",borderRadius:8,border:`1px solid ${C.bd}`,fontWeight:700,fontSize:13,background:C.s2,color:C.tx}}>🛠️ Créer</button>
            </div>
          </div>
          :progs.map(p=><ProgramCard key={p.id} prog={p} onLaunch={p=>{setActiveP(p);setTab("session");}} onDelete={id=>setProgs(prev=>prev.filter(x=>x.id!==id))}/>)
        }
      </div>}

      {/* GÉNÉRATEUR */}
      {tab==="generate"&&<div>
        {!gen?<>
          <div style={{display:"flex",gap:4,alignItems:"center",marginBottom:20}}>
            {[0,1,2].map(p=><div key={p} style={{flex:1,height:4,borderRadius:4,background:phase>=p?C.ac:C.bd,transition:"background .3s"}}/>)}
            <div style={{fontSize:11,color:C.mu,fontWeight:700,marginLeft:6,flexShrink:0}}>{phase===0?"Profil":phase===1?"Paramètres":"Split"}</div>
          </div>

          {phase===0&&<div>
            <div style={{fontSize:10,textTransform:"uppercase",letterSpacing:2,color:C.mu,marginBottom:14}}>Je m&apos;entraîne en tant que</div>
            <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:10,marginBottom:24}}>
              {[{v:"homme",e:"💪",d:"Priorités dos, épaules, pecs"},{v:"femme",e:"🌸",d:"Priorités fessiers, ischio, abdos"}].map(opt=><div key={opt.v} onClick={()=>setGender(opt.v)} style={{background:gender===opt.v?"rgba(232,255,71,.1)":C.s2,border:`2px solid ${gender===opt.v?C.ac:C.bd}`,borderRadius:12,padding:"18px 14px",cursor:"pointer",textAlign:"center"}}>
                <div style={{fontSize:32,marginBottom:8}}>{opt.e}</div>
                <div style={{fontWeight:800,fontSize:15,color:gender===opt.v?C.ac:C.tx,marginBottom:4}}>{opt.v==="homme"?"Homme":"Femme"}</div>
                <div style={{fontSize:11,color:C.mu}}>{opt.d}</div>
              </div>)}
            </div>
            <div style={{fontSize:10,textTransform:"uppercase",letterSpacing:2,color:C.mu,marginBottom:14}}>Où je m&apos;entraîne</div>
            <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:10,marginBottom:28}}>
              {[{v:"gym",e:"🏋️",l:"Salle de sport",d:"Machines, barres, câbles"},{v:"home",e:"🏠",l:"Maison",d:"Poids de corps + haltères max 8kg"}].map(opt=><div key={opt.v} onClick={()=>setLieu(opt.v)} style={{background:lieu===opt.v?"rgba(232,255,71,.1)":C.s2,border:`2px solid ${lieu===opt.v?C.ac:C.bd}`,borderRadius:12,padding:"18px 14px",cursor:"pointer",textAlign:"center"}}>
                <div style={{fontSize:32,marginBottom:8}}>{opt.e}</div>
                <div style={{fontWeight:800,fontSize:15,color:lieu===opt.v?C.ac:C.tx,marginBottom:4}}>{opt.l}</div>
                <div style={{fontSize:11,color:C.mu}}>{opt.d}</div>
              </div>)}
            </div>
            <button onClick={go1} disabled={!gender||!lieu} style={{width:"100%",padding:16,borderRadius:10,border:"none",fontWeight:800,fontSize:16,cursor:gender&&lieu?"pointer":"default",background:gender&&lieu?C.ac:"#333",color:gender&&lieu?"#000":C.mu,transition:"all .2s"}}>Suivant →</button>
          </div>}

          {phase===1&&<>
            <div style={{display:"flex",gap:8,marginBottom:18}}>
              {gender&&<div style={{background:C.s2,border:`1px solid ${C.bd}`,borderRadius:8,padding:"5px 12px",fontSize:12,fontWeight:700,color:C.ac,display:"flex",alignItems:"center",gap:6}}>{gender==="femme"?"🌸":"💪"} {gender==="femme"?"Femme":"Homme"}<button onClick={()=>setPhase(0)} style={{background:"none",border:"none",color:C.mu,fontSize:11,padding:0,cursor:"pointer"}}>✕</button></div>}
              {lieu&&<div style={{background:C.s2,border:`1px solid ${C.bd}`,borderRadius:8,padding:"5px 12px",fontSize:12,fontWeight:700,color:C.ac,display:"flex",alignItems:"center",gap:6}}>{lieu==="home"?"🏠":"🏋️"} {lieu==="home"?"Maison":"Salle"}<button onClick={()=>setPhase(0)} style={{background:"none",border:"none",color:C.mu,fontSize:11,padding:0,cursor:"pointer"}}>✕</button></div>}
            </div>
            <div style={{fontSize:10,textTransform:"uppercase",letterSpacing:2,color:C.mu,marginBottom:10}}>Priorités musculaires</div>
            <div style={{display:"grid",gridTemplateColumns:"repeat(2,1fr)",gap:8,marginBottom:20}}>
              {MC.map(m=><div key={m.id} style={{background:C.s2,border:`2px solid ${prio[m.id]?PRIOS.find(x=>x[0]===prio[m.id])?.[2]||C.bd:C.bd}`,borderRadius:10,padding:"10px 12px"}}>
                <div style={{fontWeight:600,fontSize:13,marginBottom:8}}>{m.e} {m.n}</div>
                <div style={{display:"flex",gap:4}}>{PRIOS.map(([lv,lb])=><button key={lv} style={pill(prio[m.id]===lv,lv)} onClick={()=>tP(m.id,lv)}>{lb}</button>)}</div>
              </div>)}
            </div>
            <div style={{fontSize:10,textTransform:"uppercase",letterSpacing:2,color:C.mu,marginBottom:10}}>Intensité</div>
            <div style={{display:"flex",gap:8,marginBottom:18}}>
              {[["force","FORCE","3-5 reps"],["hypertrophie","HYPER","8-12 reps"],["endurance","ENDUR.","15-20 reps"]].map(([v,l,s])=><div key={v} style={chip(type===v)} onClick={()=>setType(v)}><div style={{fontWeight:800,fontSize:14,color:C.ac}}>{l}</div><div style={{fontSize:10,color:C.mu}}>{s}</div></div>)}
            </div>
            <div style={{fontSize:10,textTransform:"uppercase",letterSpacing:2,color:C.mu,marginBottom:10}}>Séries par exercice</div>
            <div style={{display:"flex",gap:8,marginBottom:18}}>{[2,3,4].map(n=><div key={n} style={chip(sets===n)} onClick={()=>setSets(n)}><div style={{fontWeight:800,fontSize:22,color:C.ac}}>{n}</div><div style={{fontSize:10,color:C.mu}}>séries</div></div>)}</div>
            <div style={{fontSize:10,textTransform:"uppercase",letterSpacing:2,color:C.mu,marginBottom:10}}>Jours / semaine</div>
            <div style={{display:"flex",gap:8,marginBottom:24}}>{[2,3,4,5].map(n=><div key={n} style={chip(days===n)} onClick={()=>setDays(n)}><div style={{fontWeight:800,fontSize:22,color:C.ac}}>{n}</div><div style={{fontSize:10,color:C.mu}}>jours</div></div>)}</div>
            <div style={{display:"flex",gap:8}}>
              <button onClick={()=>setPhase(0)} style={{flex:1,padding:14,borderRadius:10,border:`1px solid ${C.bd}`,fontWeight:700,fontSize:14,background:"transparent",color:C.mu,cursor:"pointer"}}>← Retour</button>
              <button onClick={()=>setPhase(2)} style={{flex:2,padding:14,borderRadius:10,border:"none",fontWeight:800,fontSize:16,background:C.ac,color:"#000",cursor:"pointer"}}>Suivant →</button>
            </div>
          </>}

          {phase===2&&<>
            <div style={{fontSize:10,textTransform:"uppercase",letterSpacing:2,color:C.mu,marginBottom:14}}>Choisis ton split</div>
            {[{v:"ppl",t:"PUSH / PULL / LEGS",d:"Chaque séance cible une chaîne musculaire.",dt:"Push (pecs·épaules·triceps) · Pull (dos·biceps) · Legs (quadris·fessiers·ischio)",tg:["3j","4j","5j"]},{v:"bro",t:"BRO SPLIT",d:"Un groupe musculaire par séance, volume maximal.",dt:"Pecs+Tri · Dos+Bi · Épaules · Bras · Jambes",tg:["4j","5j"]},{v:"fullbody",t:"FULL BODY",d:"Corps entier à chaque séance.",dt:"Composés polyarticulaires, idéal pour 2-3j",tg:["2j","3j"]}].map(opt=><div key={opt.v} onClick={()=>setSplit(opt.v)} style={{background:split===opt.v?"rgba(232,255,71,.07)":C.s2,border:`2px solid ${split===opt.v?C.ac:C.bd}`,borderRadius:12,padding:"14px",marginBottom:10,cursor:"pointer"}}>
              <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:5}}>
                <div style={{fontWeight:800,fontSize:15,color:C.ac}}>{opt.t}</div>
                {split===opt.v&&<div style={{background:C.ac,color:"#000",borderRadius:20,padding:"2px 10px",fontSize:11,fontWeight:700}}>✓</div>}
              </div>
              <div style={{fontSize:12,color:C.tx,marginBottom:3}}>{opt.d}</div>
              <div style={{fontSize:11,color:C.mu,marginBottom:8}}>{opt.dt}</div>
              <div style={{display:"flex",gap:5}}>{opt.tg.map(t=><span key={t} style={{background:C.bd,borderRadius:12,padding:"2px 8px",fontSize:10,color:C.mu}}>{t}</span>)}</div>
            </div>)}
            <div style={{display:"flex",gap:8,marginTop:6}}>
              <button onClick={()=>setPhase(1)} style={{flex:1,padding:14,borderRadius:10,border:`1px solid ${C.bd}`,fontWeight:700,fontSize:14,background:"transparent",color:C.mu,cursor:"pointer"}}>← Retour</button>
              <button onClick={doGen}           style={{flex:2,padding:14,borderRadius:10,border:"none",fontWeight:800,fontSize:16,background:C.ac,color:"#000",cursor:"pointer"}}>⚡ GÉNÉRER</button>
            </div>
          </>}
        </>:<div>
          <div style={{display:"flex",gap:8,marginBottom:12}}>
            {gender&&<span style={{background:C.s2,border:`1px solid ${C.bd}`,borderRadius:8,padding:"3px 10px",fontSize:11,color:C.ac}}>{gender==="femme"?"🌸":"💪"} {gender==="femme"?"Femme":"Homme"}</span>}
            {lieu&&<span style={{background:C.s2,border:`1px solid ${C.bd}`,borderRadius:8,padding:"3px 10px",fontSize:11,color:C.ac}}>{lieu==="home"?"🏠":"🏋️"} {lieu==="home"?"Maison":"Salle"}</span>}
          </div>
          <div style={{fontWeight:700,fontSize:18,color:C.ac,marginBottom:4}}>{gen.title}</div>
          <div style={{color:C.mu,fontSize:12,marginBottom:14}}>{gen.days.length} jours · {gen.days.reduce((a,d)=>a+d.exercises.length,0)} exercices</div>
          {gen.days.map((d,di)=><div key={di} style={{background:C.s,border:`1px solid ${C.bd}`,borderRadius:10,marginBottom:10,overflow:"hidden"}}>
            <div style={{padding:"11px 14px",background:C.s2,borderBottom:`1px solid ${C.bd}`}}><div style={{fontWeight:700,fontSize:14}}>{d.name}</div><div style={{fontSize:11,color:C.mu}}>{d.focus}</div></div>
            <div style={{padding:"8px 14px"}}>{d.exercises.map((ex,ei)=><div key={ei} style={{padding:"8px 0",borderBottom:ei<d.exercises.length-1?`1px solid ${C.bd}`:"none"}}>
              <div style={{display:"flex",justifyContent:"space-between",alignItems:"flex-start"}}>
                <div style={{flex:1,minWidth:0}}>
                  <div style={{fontWeight:600,fontSize:13}}>{ex.name}</div>
                  {ex.faisceau&&<div style={{fontSize:9,color:C.ac,fontWeight:700,textTransform:"uppercase",letterSpacing:.5,marginTop:1}}>{ex.faisceau}</div>}
                  {ex.note&&<div style={{fontSize:10,color:C.mu,marginTop:2,fontStyle:"italic",lineHeight:1.4}}>{ex.note}</div>}
                </div>
                <div style={{textAlign:"right",flexShrink:0,marginLeft:10}}><span style={{fontWeight:800,fontSize:15,color:C.ac}}>{ex.sets}×</span><span style={{fontSize:11,color:C.mu,marginLeft:4}}>{ex.reps} reps</span></div>
              </div>
            </div>)}</div>
          </div>)}
          <input value={pName} onChange={e=>setPName(e.target.value)} placeholder="Nom du programme (optionnel)" style={{width:"100%",padding:"11px 14px",background:C.s2,border:`1px solid ${C.bd}`,borderRadius:9,color:C.tx,fontSize:13,marginBottom:10}}/>
          <div style={{display:"flex",gap:8}}>
            <button onClick={saveG}                            style={{flex:1,padding:14,borderRadius:10,border:"none",fontWeight:800,fontSize:15,background:C.ok,color:"#000",cursor:"pointer"}}>💾 Sauvegarder</button>
            <button onClick={()=>{setActiveP(gen);setTab("session");}} style={{flex:1,padding:14,borderRadius:10,border:"none",fontWeight:800,fontSize:15,background:C.ac,color:"#000",cursor:"pointer"}}>▶ Lancer</button>
          </div>
          <button onClick={()=>{setGen(null);setPhase(0);}} style={{width:"100%",marginTop:8,padding:11,borderRadius:10,border:`1px solid ${C.bd}`,fontWeight:600,fontSize:13,background:"transparent",color:C.mu,cursor:"pointer"}}>↩ Recommencer</button>
        </div>}
      </div>}

      {/* CRÉER */}
      {tab==="custom"&&<div>
        <input value={cName} onChange={e=>setCName(e.target.value)} placeholder="Nom de ton programme *" style={{width:"100%",padding:"11px 14px",background:C.s2,border:`1px solid ${C.bd}`,borderRadius:9,color:C.tx,fontSize:14,fontWeight:600,marginBottom:14}}/>
        <div style={{display:"flex",gap:6,marginBottom:14,alignItems:"center"}}>
          {cDays.map((d,i)=><div key={i} style={{display:"flex",alignItems:"center",gap:3}}>
            <button onClick={()=>setCDay(i)} style={{padding:"7px 13px",borderRadius:8,border:`2px solid ${i===cDay?C.ac:C.bd}`,background:i===cDay?"rgba(232,255,71,.1)":C.s2,color:i===cDay?C.ac:C.mu,fontWeight:700,fontSize:12,cursor:"pointer"}}>J{i+1} <span style={{opacity:.6}}>({d.exercises.length})</span></button>
            {cDays.length>1&&<button onClick={()=>remCD(i)} style={{background:"transparent",border:"none",color:C.mu,fontSize:14,padding:"0 2px",cursor:"pointer"}}>✕</button>}
          </div>)}
          <button onClick={addCD} style={{padding:"7px 13px",borderRadius:8,border:`2px dashed ${C.bd}`,background:"transparent",color:C.mu,fontWeight:700,fontSize:12,cursor:"pointer"}}>+ Jour</button>
        </div>
        {cDays[cDay]?.exercises.length>0&&<div style={{background:C.s,border:`1px solid ${C.bd}`,borderRadius:10,padding:"11px 13px",marginBottom:12}}>
          <div style={{fontSize:10,color:C.ac,textTransform:"uppercase",letterSpacing:1,marginBottom:8,fontWeight:700}}>Jour {cDay+1} — {cDays[cDay].exercises.length} exercice(s)</div>
          {cDays[cDay].exercises.map((ex,ei)=><div key={ei} style={{display:"flex",justifyContent:"space-between",alignItems:"center",padding:"8px 0",borderBottom:ei<cDays[cDay].exercises.length-1?`1px solid ${C.bd}`:"none"}}>
            <div><div style={{fontWeight:600,fontSize:13}}>{ex.name}</div><div style={{fontSize:10,color:C.mu}}>{ex.muscle} · {ex.reps}</div></div>
            <button onClick={()=>remEx(ei)} style={{background:"rgba(239,68,68,.1)",border:"1px solid rgba(239,68,68,.3)",color:C.hi,borderRadius:6,padding:"4px 10px",fontSize:11,fontWeight:700,cursor:"pointer"}}>✕</button>
          </div>)}
        </div>}
        <div style={{display:"flex",gap:6,marginBottom:10}}>
          {[["gym","🏋️ Salle"],["home","🏠 Maison"]].map(([v,l])=><button key={v} onClick={()=>setFLoc(v)} style={{padding:"6px 14px",borderRadius:8,border:`2px solid ${fLoc===v?C.ac:C.bd}`,background:fLoc===v?"rgba(232,255,71,.1)":"transparent",color:fLoc===v?C.ac:C.mu,fontWeight:700,fontSize:12,cursor:"pointer"}}>{l}</button>)}
        </div>
        <div style={{display:"flex",gap:5,marginBottom:10}}>
          {["Tous",...MUSCLES].map(m=><button key={m} onClick={()=>setFM(m)} style={{padding:"5px 11px",borderRadius:18,border:`1px solid ${fM===m?C.ac:C.bd}`,background:fM===m?"rgba(232,255,71,.1)":"transparent",color:fM===m?C.ac:C.mu,fontSize:11,fontWeight:600,cursor:"pointer"}}>{m}</button>)}
        </div>
        <input placeholder="🔍 Rechercher..." value={srch} onChange={e=>setSrch(e.target.value)} style={{width:"100%",padding:"9px 13px",background:C.s2,border:`1px solid ${C.bd}`,borderRadius:9,color:C.tx,fontSize:13,marginBottom:12}}/>
        <div style={{display:"grid",gridTemplateColumns:"repeat(2,1fr)",gap:8,marginBottom:16}}>
          {filtered.map(ex=><ExoCard key={ex.id} ex={ex} onAdd={addEx} added={cEN.includes(ex.name)}/>)}
        </div>
        <button onClick={savC} style={{width:"100%",padding:15,borderRadius:10,border:"none",fontWeight:800,fontSize:15,background:C.ok,color:"#000",cursor:"pointer"}}>💾 SAUVEGARDER MON PROGRAMME</button>
      </div>}

      {/* SÉANCE */}
      {tab==="session"&&(activeP
        ?<SessionTracker program={activeP} history={hist} onSave={s=>setHist(p=>[...p,s])}/>
        :<div style={{textAlign:"center",padding:"60px 20px"}}>
          <div style={{fontSize:44,marginBottom:12}}>💪</div>
          <div style={{fontWeight:700,fontSize:17,marginBottom:6}}>Aucune séance active</div>
          <div style={{color:C.mu,fontSize:13,marginBottom:20}}>Lance un programme depuis Programmes</div>
          <button onClick={()=>setTab("programs")} style={{padding:"11px 24px",borderRadius:9,border:"none",fontWeight:700,fontSize:14,background:C.ac,color:"#000",cursor:"pointer"}}>📋 Mes programmes</button>
        </div>
      )}

      {/* SUIVI */}
      {tab==="stats"&&<StatsPage history={hist}/>}

    </div>

    

    {/* Chronomètre flottant — onglet Séance uniquement */}
    {tab==="session"&&(
      <div onClick={tapTimer} style={{position:"fixed",bottom:76,right:16,zIndex:50,background:tRun?"rgba(14,14,15,.95)":"rgba(34,34,38,.95)",border:`2px solid ${tRun?C.ac:tSec>0?C.mu:C.bd}`,borderRadius:16,padding:"10px 18px",backdropFilter:"blur(12px)",cursor:"pointer",userSelect:"none",boxShadow:tRun?"0 0 20px rgba(232,255,71,.25)":"0 2px 12px rgba(0,0,0,.5)",transition:"all .2s"}}>
        <div style={{fontWeight:900,fontSize:26,color:tRun?C.ac:tSec>0?C.mu:C.tx,fontVariantNumeric:"tabular-nums",letterSpacing:2,lineHeight:1,textAlign:"center"}}>{fmt2(tSec)}</div>
        <div style={{fontSize:8,color:tRun?C.ac:C.mu,textTransform:"uppercase",letterSpacing:1.5,textAlign:"center",marginTop:3}}>{tRun?"EN COURS":"RESET"}</div>
      </div>
    )}
  </div>;
}