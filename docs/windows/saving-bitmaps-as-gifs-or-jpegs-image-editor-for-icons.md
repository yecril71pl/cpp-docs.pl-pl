---
title: Zapisywanie map bitowych jako plików GIF lub JPEG (Edytor obrazów dla ikon)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.image.editing
helpviewer_keywords:
- .gif files [C++], saving bitmaps as
- jpg files [C++], saving bitmaps as
- jpeg files [C++], saving bitmaps as
- .jpg files [C++], saving bitmaps as
- Image editor [C++], converting image formats
- gif files [C++], saving bitmaps as
- bitmaps [C++], converting formats
- .jpeg files [C++], saving bitmaps as
- graphics [C++], converting formats
- images [C++], converting formats
ms.assetid: 115df69f-10fb-4e6f-906b-853c1e4a54af
ms.openlocfilehash: 99b083236f935bc02acef46d6620256416df93a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592832"
---
# <a name="saving-bitmaps-as-gifs-or-jpegs-image-editor-for-icons"></a>Zapisywanie map bitowych jako plików GIF lub JPEG (Edytor obrazów dla ikon)

Gdy tworzysz mapę bitową, obraz jest tworzony w formacie mapy bitowej (bmp). Można jednak zapiszesz obraz GIF lub JPEG lub w innych formatach grafiki.

> [!NOTE]
> Ten proces nie ma zastosowania do ikony i kursory.

### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>Aby utworzyć i zapisać mapy bitowej jako obraz GIF lub JPEG

1. Z **pliku** menu, wybierz **Otwórz**, następnie kliknij przycisk **pliku**.

2. W **okno dialogowe Nowy plik**, kliknij przycisk **Visual C++** folderu, następnie wybierz pozycję **plik mapy bitowej (bmp)** w **szablony** pole, a następnie kliknij przycisk  **Otwórz**.

   Mapa bitowa zostanie otwarty w **obraz** edytora.

3. Wprowadź zmiany do nowej mapy bitowej, zgodnie z potrzebami.

4. Z mapą bitową wciąż otwarty w **obraz** edytorze kliknij **Zapisz *filename*.bmp jako** na **pliku** menu.

5. W **Zapisz plik jako** okna dialogowego wpisz nazwę, którą chcesz nadać pliku i rozszerzenie, które określa format pliku, w **nazwy pliku** pole. Na przykład *myfile.gif*.

   > [!NOTE]
   > Należy utworzyć lub otworzyć mapy bitowej spoza projektu, aby można było zapisać go jako pliku w innym formacie. Jeśli tworzysz lub otwórz go w swoim projekcie **Zapisz jako** polecenie jest niedostępne. Aby uzyskać więcej informacji, zobacz [wyświetlania zasobów w zasobu skryptu pliku poza z projektu (autonomicznego)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

6. Kliknij przycisk **Zapisz**.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="see-also"></a>Zobacz też

[Edytowanie zasobów graficznych](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)