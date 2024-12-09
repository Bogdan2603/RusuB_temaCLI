# RusuB_tema09

Descrieti diferentele dintre iluminarea asa cum functioneaza in lumea reala si modelul de iluminare utilizat de OpenGL.

In lumea reala, iluminarea este foarte complexa, incluzand reflexii, refractii si dispersii multiple, iar fiecare foton are un impact asupra scenei. In schimb, in OpenGL, lucrurile sunt simplificate. Se folosesc modele matematice precum Phong sau Blinn-Phong, care aproximeaza doar anumite tipuri de reflexii, cum ar fi cele ambientale, difuze si speculare, fara a calcula toata traiectoria luminii.

Cate surse de lumina sunt suportate in implementarea curenta a OpenGL cu ajutorul framework-ului OpenTK?

Numărul exact poate varia in functie de implementare si de versiunea OpenGL folosita, dar in general, OpenGL suporta cel putin 8 surse de lumina. Pentru a fi sigur, e bine sa verifici acest detaliu in codul proiectului tau.

Definiti iluminarea de material si specificati unde si cand este utilizata aceasta.

Iluminarea de material se refera la efectele de lumina integrate in textura sau materialul unui obiect 3D. De exemplu, un material poate avea emisivitate, ceea ce inseamna ca poate parea ca lumineaza singur. Este folosita pentru a crea efecte speciale, cum ar fi simulari de LED-uri sau obiecte stralucitoare, dar si pentru a adauga un plus de realism scenelor.

Care este efectul asupra diverselor obiecte la activarea unei surse de lumina secundare (per pct. 3), comparativ cu utilizarea unei singure surse de lumina?

O sursa de lumina secundara aduce mai multa complexitate si realism in scena. Apar umbre suplimentare, iluminarea devine mai variata si reflexiile mai realiste, ceea ce face ca obiectele sa para mai tridimensionale. Cu o singura sursa de lumina, scena poate parea mai plata si mai simpla.