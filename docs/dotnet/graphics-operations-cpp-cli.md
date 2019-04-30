---
title: Operacje graficzne (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- GDI+ [C++]
- .NET Framework [C++], graphics
- images [C++], .NET Framework and
- GDI+ [C++], about graphics operations
- graphics [C++], .NET Framework and
- GDI+ [C++], displaying images
- graphics [C++], displaying images
- GDI+, drawing shapes
- drawing, shapes
- shapes
- shapes, drawing
- GDI+ [C++], rotating images
- graphics [C++], rotating images
- GDI+ [C++], converting image file formats
- graphics [C++], converting image file formats
ms.assetid: bba27228-b9b3-4c9c-b31c-a04b76702a95
ms.openlocfilehash: c7c6d62eb4059069e6e266544ce6323c63dd15c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393743"
---
# <a name="graphics-operations-ccli"></a>Operacje graficzne (C++/CLI)

Pokazuje manipulowania obrazu za pomocą zestawu Windows SDK.

W poniższych tematach pokazano użycie <xref:System.Drawing.Image?displayProperty=fullName> klasy, aby wykonywać operacje na obrazie.

## <a name="display"></a> Wyświetlanie obrazów za pomocą programu .NET Framework

Poniższy przykład kodu zmienia program obsługi zdarzeń OnPaint wskaźnik, aby pobrać <xref:System.Drawing.Graphics> obiektu dla tego formularza. <xref:System.Windows.Forms.Form.OnPaint%2A> Funkcji jest przeznaczona dla aplikacji Windows Forms, najprawdopodobniej utworzone za pomocą Kreatora aplikacji Visual Studio.

Obraz, który jest reprezentowany przez <xref:System.Drawing.Image> klasy. Dane obrazu są ładowane z pliku jpg przy użyciu <xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName> metody. Przed narysowaniem obrazu do formularza, rozmiarów formularza do pomieszczenia obrazu. Rysowanie obrazu odbywa się za pomocą <xref:System.Drawing.Graphics.DrawImage%2A?displayProperty=fullName> metody.

<xref:System.Drawing.Graphics> i <xref:System.Drawing.Image> klasy znajdują się w <xref:System.Drawing?displayProperty=fullName> przestrzeni nazw.

### <a name="example"></a>Przykład

```cpp
#using <system.drawing.dll>

using namespace System;
using namespace System::Drawing;

protected:
virtual Void Form1::OnPaint(PaintEventArgs^ pe) override
{
    Graphics^ g = pe->Graphics;
    Image^ image = Image::FromFile("SampleImage.jpg");
    Form::ClientSize = image->Size;
    g->DrawImage( image, 0, 0, image->Size.Width, image->Size.Height );
}
```

## <a name="draw"></a> Rysowanie kształtów za pomocą programu .NET Framework

Poniższy przykład kodu wykorzystuje <xref:System.Drawing.Graphics> klasy, aby zmodyfikować <xref:System.Windows.Forms.Form.OnPaint%2A> programu obsługi zdarzeń do pobrania wskaźnika do <xref:System.Drawing.Graphics> obiektu dla tego formularza. This, wskaźnik jest następnie używany do Ustaw kolor tła formularza i rysowanie linii i usługi za pomocą łuk <xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName> i <xref:System.Drawing.Graphics.DrawArc%2A> metody.

### <a name="example"></a>Przykład

```cpp
#using <system.drawing.dll>
using namespace System;
using namespace System::Drawing;
// ...
protected:
virtual Void Form1::OnPaint(PaintEventArgs^ pe ) override
{
   Graphics^ g = pe->Graphics;
   g->Clear(Color::AntiqueWhite);

   Rectangle rect = Form::ClientRectangle;
   Rectangle smallRect;
   smallRect.X = rect.X + rect.Width / 4;
   smallRect.Y = rect.Y + rect.Height / 4;
   smallRect.Width = rect.Width / 2;
   smallRect.Height = rect.Height / 2;

   Pen^ redPen = gcnew Pen(Color::Red);
   redPen->Width = 4;
   g->DrawLine(redPen, 0, 0, rect.Width, rect.Height);

   Pen^ bluePen = gcnew Pen(Color::Blue);
   bluePen->Width = 10;
   g->DrawArc( bluePen, smallRect, 90, 270 );
}
```

## <a name="rotate"></a> Obracanie obrazów za pomocą programu .NET Framework

Poniższy przykład kodu demonstruje użycie <xref:System.Drawing.Image?displayProperty=fullName> klasy, aby załadować obraz z dysku, Obróć go o 90 stopni i zapisz go jako nowy plik jpg.

### <a name="example"></a>Przykład

```cpp
#using <system.drawing.dll>

using namespace System;
using namespace System::Drawing;

int main()
{
   Image^ image = Image::FromFile("SampleImage.jpg");
   image->RotateFlip( RotateFlipType::Rotate90FlipNone );
   image->Save("SampleImage_rotated.jpg");
   return 0;
}
```

## <a name="convert"></a> Konwertowanie formatów plików obrazów za pomocą programu .NET Framework

Poniższy przykład kodu demonstruje <xref:System.Drawing.Image?displayProperty=fullName> klasy i <xref:System.Drawing.Imaging.ImageFormat?displayProperty=fullName> wyliczenie służące do konwertowania i Zapisz pliki obrazów. Poniższy kod ładuje obraz z pliku jpg i zapisuje go w formatach plików GIF i BMP.

### <a name="example"></a>Przykład

```cpp
#using <system.drawing.dll>

using namespace System;
using namespace System::Drawing;
using namespace System::Drawing::Imaging;

int main()
{
   Image^ image = Image::FromFile("SampleImage.jpg");
   image->Save("SampleImage.png", ImageFormat::Png);
   image->Save("SampleImage.bmp", ImageFormat::Bmp);

   return 0;
}
```

## <a name="related-sections"></a>Sekcje pokrewne

[Wprowadzenie do programowania grafiki](/dotnet/framework/winforms/advanced/getting-started-with-graphics-programming)

[Informacje o kodzie zarządzanym GDI+](/dotnet/framework/winforms/advanced/about-gdi-managed-code)

## <a name="see-also"></a>Zobacz także

[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

<xref:System.Drawing>
