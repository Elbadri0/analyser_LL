# analyser_LL

## Voici quelques-unes des hypothèses que j'ai faites: -

1) Epsilon est représenté par '#'.
2) Les productions sont de la forme A = B, où «A» est un seul non-terminal et «B» peut être n'importe quelle combinaison de terminaux et de non-terminaux.
2) Grammer n'est pas laissé récursif.
5) Chaque production d'un non terminal est inscrite sur une ligne différente.
6) Seules les lettres majuscules sont des non-terminaux et tout le reste est un terminal.
7) N'utilisez pas '!' ou «$» car ils sont réservés à des fins spéciales.
8) Toutes les chaînes d'entrée doivent se terminer par un '$'.

---------------------------------------------------------------------

on va etiliser un exercice fait en class
nb:
J it's E'
S it's T'
first=premier
follow= suivant
---------------------------------------------------------------------
nombre des productions ? :8

Enter les 8  productions sous la form A=B d'ou A et B sont des symbole de grammaire :

E=TJ 

J=+TJ

J=#

T=FS

S=*FS

S=#

F=(E)

F=a

-----------------------------------------------
 First(E)= { (, a, }

 First(J)= { +, #, }

 First(T)= { (, a, }

 First(S)= { *, #, }

 First(F)= { (, a, }

-----------------------------------------------

 Follow(E) = { $, ),  }

 Follow(J) = { $, ),  }

 Follow(T) = { +, $, ),  }

 Follow(S) = { +, $, ),  }

 Follow(F) = { *, +, $, ),  }

-----------------------------------------------

                    la Table d'analyse de L'analyseur LL(1) de ce grammair:-                        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

==================================================================================================
  		|       +               *               (               )               a       	 $
==================================================================================================
   E    |                                       E=TJ                            E=TJ
--------------------------------------------------------------------------------------------------
   J    |       J=+TJ                                           J=#							J=#
--------------------------------------------------------------------------------------------------
   T    |                                       T=FS                            T=FS
--------------------------------------------------------------------------------------------------
   S    |       S=#             S=*FS                           S=#							S=#
--------------------------------------------------------------------------------------------------
   F    |                                       F=(E)                           F=a
--------------------------------------------------------------------------------------------------



Mot d’entrée : (a*a)
 ===========================================================================
           Stack                   Input                   Action
===========================================================================
            $E                      (a*a)$                  E=TJ
            $JT                     (a*a)$                  T=FS
            $JSF                    (a*a)$                  F=(E)
            $JS)E(                  (a*a)$                  POP ACTION
            $JS)E                   a*a)$                   E=TJ
            $JS)JT                  a*a)$                   T=FS
            $JS)JSF                 a*a)$                   F=a
            $JS)JSa                 a*a)$                   POP ACTION
            $JS)JS                  *a)$                    S=*FS
            $JS)JSF*                *a)$                    POP ACTION
            $JS)JSF                 a)$                     F=a
            $JS)JSa                 a)$                     POP ACTION
            $JS)JS                  )$                      S=#
            $JS)J                   )$                      J=#
            $JS)                    )$                      POP ACTION
            $JS                     $                       S=#
            $J                      $                       J=#
            $                       $                       POP ACTION

========================================================================================
                            YOUR STRING HAS BEEN ACCEPTED !!
====================================================================================