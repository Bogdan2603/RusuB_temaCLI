# RusuB_tema03

1.Ordinea de desenare a vârfurilor: Pentru metodele de desenare OpenGL, ordinea poate fi orară sau anti-orară, specificată de programator. Axele de coordonate se pot desena folosind un singur apel GL.Begin(), specificând vârfurile pentru fiecare axă.

2.Anti-aliasing: Este o tehnică ce reduce efectul de „scăriță” de pe marginile obiectelor, creând un aspect mai neted prin amestecarea culorilor între obiect și fundal.

3.Efectul GL.LineWidth(float) și GL.PointSize(float): GL.LineWidth(float) schimbă grosimea liniilor, iar GL.PointSize(float) modifică dimensiunea punctelor. Ambele funcționează în interiorul unui apel GL.Begin().

4.Directiva LineLoop: Crează o buclă de linii conectând ultimul punct cu primul.
Directiva LineStrip: Desenează o linie continuă între toate punctele.
Directiva TriangleFan: Desenează triunghiuri folosind un punct comun și toate punctele adiacente.
Directiva TriangleStrip: Desenează o secvență de triunghiuri unde fiecare triunghi împarte două vârfuri cu cel anterior.

6.Culori diferite la obiecte 3D: Utilizarea culorilor diverse ajută la diferențierea fețelor și contururilor obiectelor, oferind un aspect mai realist.

7.Gradient de culoare: Gradientul este o trecere lină între culori. În OpenGL, gradientul se creează setând culori diferite pentru fiecare vârf.

8.

*****

using OpenTK;
using OpenTK.Graphics.OpenGL;
using OpenTK.Input;
using System;
using System.Drawing;
using [System.IO](http://system.io/);
using System.Globalization;

namespace LabApp
{
internal class TriangleApp : GameWindow
{
private Vector3[] triangleVertices = new Vector3[3];
private Color color = Color.FromArgb(255, 255, 0, 0); // Roșu complet opac
private float rotationX = 0f;
private float rotationY = 0f;
private int colorChannel = 0; // 0 = Red, 1 = Green, 2 = Blue

```
    public TriangleApp() : base(800, 600)
    {
        VSync = VSyncMode.On;
        LoadTriangleVertices("triangle.txt");
    }

    private void LoadTriangleVertices(string filePath)
    {
        // Încarcă coordonatele triunghiului dintr-un fișier text
        string[] lines = File.ReadAllLines(filePath);
        for (int i = 0; i < 3; i++)
        {
            string[] parts = lines[i].Split(' ');
            triangleVertices[i] = new Vector3(
                float.Parse(parts[0], CultureInfo.InvariantCulture),
                float.Parse(parts[1], CultureInfo.InvariantCulture),
                float.Parse(parts[2], CultureInfo.InvariantCulture)
            );
        }
    }

    protected override void OnLoad(EventArgs e)
    {
        base.OnLoad(e);
        GL.ClearColor(Color.Black);
        GL.Enable(EnableCap.DepthTest);
    }

    protected override void OnResize(EventArgs e)
    {
        base.OnResize(e);
        GL.Viewport(0, 0, Width, Height);

        Matrix4 projection = Matrix4.CreatePerspectiveFieldOfView(MathHelper.PiOver4, Width / (float)Height, 0.1f, 100f);
        GL.MatrixMode(MatrixMode.Projection);
        GL.LoadMatrix(ref projection);
    }

    protected override void OnUpdateFrame(FrameEventArgs e)
    {
        base.OnUpdateFrame(e);
        KeyboardState keyboard = Keyboard.GetState();

        // Modifică culoarea triunghiului cu tastele R, G, B
        if (keyboard[Key.R])
            color = Color.FromArgb(color.A, Math.Min(255, color.R + 10), color.G, color.B);
        if (keyboard[Key.G])
            color = Color.FromArgb(color.A, color.R, Math.Min(255, color.G + 10), color.B);
        if (keyboard[Key.B])
            color = Color.FromArgb(color.A, color.R, color.G, Math.Min(255, color.B + 10));

        // Modifică canalul de transparență
        if (keyboard[Key.T])
            color = Color.FromArgb(Math.Max(0, color.A - 10), color.R, color.G, color.B);

        // Ieșire cu Esc
        if (keyboard[Key.Escape])
            Exit();
    }

    protected override void OnMouseMove(MouseMoveEventArgs e)
    {
        // Modifică unghiul camerei în funcție de mișcarea mouse-ului
        rotationX += e.YDelta * 0.2f;
        rotationY += e.XDelta * 0.2f;
    }

    protected override void OnRenderFrame(FrameEventArgs e)
    {
        base.OnRenderFrame(e);
        GL.Clear(ClearBufferMask.ColorBufferBit | ClearBufferMask.DepthBufferBit);

        // Setează matricea de modelview
        GL.MatrixMode(MatrixMode.Modelview);
        GL.LoadIdentity();
        GL.Translate(0.0, 0.0, -5.0);
        GL.Rotate(rotationX, 1.0, 0.0, 0.0);
        GL.Rotate(rotationY, 0.0, 1.0, 0.0);

        // Desenează triunghiul cu culoarea specificată
        GL.Begin(PrimitiveType.Triangles);
        GL.Color4(color);

        foreach (var vertex in triangleVertices)
        {
            GL.Vertex3(vertex);
        }

        GL.End();

        SwapBuffers();
    }
}

```

}

***********

10.

Utilizarea unor culori diferite pentru fiecare vertex în desenarea unei linii sau triunghiuri în modul strip permite:

Gradienți: Creează tranziții de culoare vizuale.
Iluminare: Simulează efecte de iluminare mai realiste.
Mișcare: Animațiile devin mai atractive.
Diferentiere: Ajută la identificarea rapidă a elementelor.
Texturare: Îmbunătățește detaliile vizuale.
Antialiasing: Estompează marginile ascuțite.
