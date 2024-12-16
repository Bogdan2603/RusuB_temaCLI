# RusuB_tema10

Care este rolul comenzilor GL.Push() și GL.Pop()? De ce este necesară utilizarea lor?
GL.PushMatrix() salvează starea curentă a matricei de modelare-vizualizare pe o stivă.
GL.PopMatrix() restaurează ultima stare salvată a matricei de pe stivă.
Utilitate: Aceste comenzi sunt necesare pentru a salva și restaura transformările curente într-o scenă complexă. Ele sunt folosite în special în manipulările ierarhice, cum ar fi desenarea unor obiecte care depind unul de altul, dar care necesită transformări independente (de exemplu, un braț robotizat cu mai multe piese).

Explicați efectul rulării metodelor GL.Rotate(), GL.Translate() și GL.Scale(). Furnizați câte un exemplu comentat!
GL.Rotate(angle, x, y, z): Aplică o rotație în jurul axei (x, y, z) cu un unghi specificat.
Exemplu: GL.Rotate(45.0f, 0.0f, 1.0f, 0.0f); → Rotește obiectul cu 45 de grade în jurul axei Oy.
GL.Translate(x, y, z): Deplasează obiectul cu (x, y, z) pe axele respective.
Exemplu: GL.Translate(2.0f, 0.0f, -5.0f); → Deplasează obiectul 2 unități pe Ox și -5 unități pe Oz.
GL.Scale(x, y, z): Aplică o scalare (mărire/micșorare) pe axele (x, y, z).
Exemplu: GL.Scale(2.0f, 1.0f, 1.0f); → Dublează dimensiunea obiectului pe axa Ox.
Comentariu: Aceste metode sunt aplicate matricei curente, modificând poziția, orientarea sau dimensiunea obiectelor desenate.

Câte nivele de manipulări ierarhice (folosindu-se GL.Push()/GL.Pop()) suportă o scenă OpenGL?
OpenGL specifică o stivă de matrice pentru manipulări ierarhice. Adâncimea maximă a stivei pentru matricea model-view poate varia, dar implementările OpenGL garantează un minim de 32 de nivele pentru stiva de modelare-vizualizare.