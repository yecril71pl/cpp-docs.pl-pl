---
title: Tworzenie pędzla niestandardowego (Edytor obrazów dla ikon)
ms.date: 11/04/2016
helpviewer_keywords:
- colors [C++], brush
- brushes, colors
- brushes, creating custom
- images [C++], creating custom brushes
- graphics [C++], custom brushes
- custom brushes
ms.assetid: 750881aa-6f47-4de9-8ca6-a7a12afc6383
ms.openlocfilehash: 01d5badc70aac3e51a8731c5ea62b30a27d2962a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502859"
---
# <a name="creating-a-custom-brush-image-editor-for-icons"></a>Tworzenie pędzla niestandardowego (Edytor obrazów dla ikon)

Niestandardowy obiekt brush jest prostokątny fragment obrazu, które przejmą i używać jak jeden z **obraz** edytora pędzle gotowych do użycia. Wszystkie operacje, które można wykonywać na wybranych, można wykonywać na niestandardowy obiekt brush także.

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>Aby utworzyć niestandardowy obiekt brush z części obrazu

1. [Wybierz część obrazu](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) , którą chcesz używać dla pędzla.

2. Przytrzymanie **Shift** klucza w dół, kliknij w zaznaczeniu i przeciągnij go na obrazie.

   \- lub —

3. Z **obraz** menu, wybierz **Użyj zaznaczenia jako pędzla**.

   Wybór staje się pędzla niestandardowego, który rozdziela kolorów w wyborze między obrazu. Kopiuje zaznaczenie są pozostawiane w ścieżce przeciągania. Przeciągniesz wolniej, większej liczby kopii zostały wprowadzone.

   > [!NOTE]
   > Klikając **Użyj zaznaczenia jako pędzla** bez polega na wybraniu część obrazu użyje całego obrazu jako pędzla. Wynik za pomocą niestandardowy obiekt brush również będzie zależeć od tego, czy wybrano [tła nieprzezroczyste lub przezroczyste](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Niestandardowy obiekt brush pikseli, które odpowiadają bieżącym kolorem tła są zwykle przezroczyste: one nie malowanie istniejącego obrazu. Można zmienić to zachowanie, tak aby pikseli kolor tła malować przez istniejący obraz.

Niestandardowy obiekt brush sygnaturę lub wzornika służy do tworzenia szerokiej gamy efekty specjalne.

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>Do rysowania kształtów niestandardowy obiekt brush kolor tła

1. [Wybierz tło nieprzezroczyste lub przezroczyste](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

2. [Ustaw kolor tła](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) kolor, w której chcemy narysować.

3. Ustaw niestandardowy obiekt brush, w której chcemy narysować.

4. Kliknij prawym przyciskiem myszy. Wszelkie nieprzezroczyste regionów niestandardowy obiekt brush są rysowane w kolor tła.

### <a name="to-double-or-halve-the-custom-brush-size"></a>Dwukrotnie lub połowę rozmiar niestandardowy obiekt brush

1. Naciśnij klawisz **znak Plus** (**+**) klucz dwukrotnie rozmiar pędzla lub **znak Minus** (**-**) kluczem o połowę go .

### <a name="to-cancel-the-custom-brush"></a>Aby anulować niestandardowy obiekt brush

1. Naciśnij klawisz **Esc** lub innego narzędzia do rysowania.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Edytowanie zasobów graficznych](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)