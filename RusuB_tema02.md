# RusuB_tema02

Ce este un viewport?

În OpenGL, un viewport definește zona ecranului unde va fi afișată imaginea generată. Este o secțiune dreptunghiulară în care coordonatele din OpenGL sunt transformate pentru a se potrivi dimensiunilor ecranului.
Ce reprezintă conceptul de frames per second din punctul de vedere al bibliotecii OpenGL?

Frames per second (FPS) măsoară câte cadre sunt afișate pe ecran într-o secundă. În OpenGL, acest lucru indică cât de des este actualizată și redată scena grafică, afectând fluiditatea mișcărilor.
Când este rulată metoda OnUpdateFrame()?

Această metodă este de obicei apelată la fiecare cadru pentru a actualiza starea aplicației, cum ar fi pozițiile obiectelor sau animațiile, înainte ca scena să fie randată.
Ce este modul imediat de randare?

Modul imediat de randare este un mod simplu de a trimite comenzi de desenare direct la GPU, dar este mai puțin eficient decât metodele moderne, cum ar fi utilizarea de vertex buffers.
Care este ultima versiune de OpenGL care acceptă modul imediat?

OpenGL a început să deprecieze modul imediat începând cu versiunea 3.0, dar acesta este încă disponibil în versiunile mai vechi.
Când este rulată metoda OnRenderFrame()?

Această metodă este apelată la fiecare cadru pentru a desena scena pe ecran după ce starea aplicației a fost actualizată.
De ce este nevoie ca metoda OnResize() să fie executată cel puțin o dată?

Metoda OnResize() trebuie rulată atunci când fereastra se modifică în dimensiuni, pentru a ajusta scena grafică astfel încât să fie afișată corect în noile dimensiuni.
Ce reprezintă parametrii metodei CreatePerspectiveFieldOfView() și care este domeniul de valori pentru aceștia?

Metoda creează o matrice de proiecție pentru perspectiva vederii. Parametrii includ:
Field of View (FOV): unghiul de vizualizare, care influențează câmpul vizual vertical.
Aspect ratio: raportul între lățime și înălțime.
Near plane și Far plane: distanțele minime și maxime la care obiectele sunt vizibile.
FOV variază între 30 și 120 de grade, iar valorile pentru near și far plane trebuie să fie pozitive și separate.
