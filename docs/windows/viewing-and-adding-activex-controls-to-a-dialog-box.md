---
title: Wyświetlanie i dodawanie kontrolek ActiveX do okna dialogowego (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.controls.activex
- vc.editors.dialog.insertActiveXControls
helpviewer_keywords:
- dialog boxes [C++], adding ActiveX controls
- ActiveX controls [C++], adding to dialog boxes
- Insert ActiveX Control dialog box [C++]
- controls [C++], editing properties
- ActiveX controls [C++], properties
ms.assetid: e1c2e3ae-e1b0-40d3-9766-623007073856
ms.openlocfilehash: 139407ec1d4e1bfad6bb06854dc24b86ce7014e8
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293614"
---
# <a name="viewing-and-adding-activex-controls-to-a-dialog-box-c"></a>Wyświetlanie i dodawanie kontrolek ActiveX do okna dialogowego (C++)

Program Visual Studio umożliwia wstawianie kontrolki ActiveX z okna dialogowego.

**Wstawianie formantu ActiveX** okno dialogowe umożliwia wstawianie kontrolki ActiveX dialogowym podczas korzystania z [Edytor okien dialogowych](../windows/dialog-editor.md). To okno dialogowe zawiera następujące właściwości:

|Właściwość|Opis|
|---|---|
|**ActiveX Control**|Wyświetla listę formantów ActiveX. Wstawianie kontrolki z tego okna dialogowego nie generuje klasę otoki. Klasa otoki, należy użyć [Widok klas](/visualstudio/ide/viewing-the-structure-of-code) ją utworzyć (Aby uzyskać więcej informacji, zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md)). Jeśli formant ActiveX nie ma w tym oknie dialogowym, spróbuj zainstalować kontroli zgodnie z instrukcjami dostawcy.|
|**Path**|Wyświetla plik, w którym znajduje się Kontrolka ActiveX.|

Możesz umieścić formantów w **przybornika** okna, aby mieć łatwy dostęp. Aby uzyskać więcej informacji, zobacz [przybornika](/visualstudio/ide/reference/).

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-see-the-activex-controls-you-have-available"></a>Aby wyświetlić kontrolki ActiveX masz dostępne

1. Otwórz okno dialogowe, w edytorze okien dialogowych.

1. Kliknij prawym przyciskiem myszy w dowolnym miejscu w treści okno dialogowe.

1. W menu skrótów wybierz **Wstawianie formantu ActiveX**.

   **Wstawianie formantu ActiveX** pojawi się okno dialogowe, przedstawiający wszystkie formanty ActiveX w Twoim systemie. W dolnej części okna dialogowego jest wyświetlana ścieżka do pliku formantu ActiveX.

## <a name="to-add-an-activex-control-to-a-dialog-box"></a>Aby dodać formant ActiveX do okna dialogowego

1. W **Wstawianie formantu ActiveX** okna dialogowego wybierz kontrolkę, o których chcesz dodać do swojej okno dialogowe, a następnie wybierz pozycję **OK**.

   Formant ma być wyświetlany w oknie dialogowym, w którym można go edytować lub tworzyć programy obsługi dla niego tak samo, jak dowolną inną kontrolką.

   > [!NOTE]
   > Można dodać formanty ActiveX do [okno przybornika](/visualstudio/ide/reference/toolbox).

   > [!CAUTION]
   > Może nie być prawne rozpowszechnianie wszystkich kontrolek ActiveX w Twoim systemie. Zapoznaj się z umową licencyjną dotyczącą oprogramowania, zainstalowanego kontrolki lub skontaktuj się z firmą oprogramowania.

   Możesz umieścić formantów w **przybornika** okna, aby mieć łatwy dostęp. Aby uzyskać więcej informacji, zobacz [przybornika](/visualstudio/ide/reference/toolbox).

## <a name="to-edit-properties-for-an-activex-control"></a>Aby edytować właściwości kontrolki ActiveX

Kontrolki ActiveX, dostarczone przez niezależnych dostawców może są wyposażone w ich własnych właściwości i właściwości. Właściwości formantów ActiveX są wyświetlane w **właściwości** okna. Ponadto wszystkie strony właściwości utworzone przez autorów formantu ActiveX są wyświetlane w **strony właściwości** okno dialogowe (Aby wyświetlić **strona właściwości** określonej kontrolki ActiveX, kliknij przycisk  **Strona właściwości** znajdujący się w [okno właściwości](/visualstudio/ide/reference/properties-window)).

Na stronie właściwości dla formantu ActiveX, w zależności od arkuszy właściwości, które pochodzą z formantu ActiveX w ramach będą wyświetlane różne karty.

> [!NOTE]
> Poniższa procedura ma zastosowanie przy użyciu strony właściwości, aby edytować kontrolki ActiveX. Możesz również przeglądać i edytować właściwości formantu ActiveX w nowym **właściwości** okna.

1. Wybierz **ActiveX** kontroli.

1. Na **widoku** menu, wybierz opcję **strona właściwości** i Wyświetl właściwości.

1. W razie potrzeby na stronie właściwości, należy wprowadzić zmiany.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)<br/>
[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)<br/>
[Wyświetlanie i dodawanie kontrolek ActiveX do okna dialogowego](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)<br/>
[Karta Edytor okien dialogowych, Przybornik](../windows/dialog-editor-tab-toolbox.md)<br/>
[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
