---
title: Edytowanie części obrazu (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], editing images
- Clipboard [C++], pasting
- images [C++], editing
- images [C++], deleting selected parts
- images [C++], copying selected parts
- images [C++], moving selected parts
- images [C++], dragging and replicating selected parts
- images [C++], pasting into
- graphics [C++], editing
ms.assetid: ff4f5fef-71a4-4fd8-825e-049399fed391
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9340180049d85b1b5385d49c7b358c3fd791ce9d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391478"
---
# <a name="editing-parts-of-an-image-image-editor-for-icons"></a>Edytowanie części obrazu (Edytor obrazów dla ikon)

Można wykonywać operacje edycji standard — wycinanie, kopiowanie, czyszczenie i przenoszenie — na [wybór](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)na to, czy zaznaczenie jest całego obrazu lub po prostu jego część. Ponieważ **obraz** Edytor używa **Schowka Windows**, mogą przesyłać obrazy między **obraz** edytora i inne aplikacje dla Windows.

Ponadto możesz zmienić rozmiar zaznaczenia, czy obejmuje cały obraz lub po prostu części.

### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>Wytnij bieżącego zaznaczenia i przenieś go do Schowka

1. Kliknij przycisk **Wytnij** na **Edytuj** menu.

### <a name="to-copy-the-selection"></a>Aby skopiować zaznaczenie

1. Umieść kursor wewnątrz obramowania zaznaczenia lub dowolnego miejsca na nim, z wyjątkiem uchwytów zmiany rozmiaru.

2. Naciśnij i przytrzymaj **Ctrl** klucza jako przeciągnij je do nowej lokalizacji. Obszar oryginalnego zaznaczenia pozostaje niezmieniony.

3. Aby skopiować zaznaczenie do obrazu w jego bieżącej lokalizacji, kliknij poza kursor wyboru.

### <a name="to-paste-the-clipboard-contents-into-an-image"></a>Wklej zawartość Schowka do obrazu

1. Z **Edytuj** menu, wybierz **Wklej**.

   Zawartość Schowka otoczone obramowaniem zaznaczenia, są wyświetlane w lewym górnym rogu okienka.

2. Umieść kursor w granicach obramowania zaznaczenia, a następnie przeciągnij obraz do żądanej lokalizacji na obrazie.

3. Aby móc zakotwiczyć obrazu w nowej lokalizacji, kliknij poza krawędź zaznaczenia.

### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>Aby usunąć bieżące zaznaczenie bez przenoszenia go do Schowka

1. Z **Edytuj** menu, wybierz **Usuń**.

   Oryginalny obszar zaznaczenia jest wypełniany z bieżącym kolorem tła.

   > [!NOTE]
   > Możesz uzyskać dostęp **Wytnij**, **kopiowania**, **Wklej**, i **Usuń** polecenia, klikając prawym przyciskiem myszy w **widok zasobów** okna.

### <a name="to-move-the-selection"></a>Aby przenieść zaznaczenie

1. Umieść kursor wewnątrz obramowania zaznaczenia lub dowolnego miejsca na nim, z wyjątkiem uchwytów zmiany rozmiaru.

2. Przeciągnij zaznaczenie do nowej lokalizacji.

3. Aby móc zakotwiczyć zaznaczenia w obrazie w nowej lokalizacji, kliknij poza krawędź zaznaczenia.

Aby uzyskać więcej informacji na temat rysowanie przy zaznaczeniem, zobacz [Tworzenie pędzla niestandardowego](../windows/creating-a-custom-brush-image-editor-for-icons.md).

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Edytowanie zasobów graficznych](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)