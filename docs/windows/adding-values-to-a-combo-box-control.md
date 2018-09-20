---
title: Dodawanie wartości do kontrolki pola kombi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.combo
dev_langs:
- C++
helpviewer_keywords:
- combo boxes [C++], Data property
- controls [C++], testing values in combo boxes
- combo boxes [C++], adding values
- combo boxes [C++], previewing values
- Data property
- combo boxes [C++], testing values
ms.assetid: 22a78f98-fada-48b3-90d8-7fa0d8e4de51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0812c05844bbff9d6a341ea5b5812c5e328c2d5b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373376"
---
# <a name="adding-values-to-a-combo-box-control"></a>Dodawanie wartości do kontrolki pola kombi

Możesz dodać wartości do kontrolki pola kombi, tak długo, jak masz **okna dialogowego** edytorze.

> [!TIP]
> To dobry pomysł, aby dodać wszystkie wartości do pola kombi *przed* rozmiar, w tym polu **okna dialogowego** edytora lub użytkownik może obciąć tekst, który powinien zostać wyświetlony w kontrolce kombi.

### <a name="to-enter-values-into-a-combo-box-control"></a>Aby wprowadzić wartości do kontrolki pola kombi

1. Zaznacz formant pola kombi, klikając ją.

2. W [okno właściwości](/visualstudio/ide/reference/properties-window), przewiń w dół do **danych** właściwości.

   > [!NOTE]
   > W przypadku wyświetlania właściwości pogrupowane według typu, **danych** pojawia się w **różne** właściwości.

3. Kliknij opcję w obszarze wartości w celu **danych** właściwości i wpisz wartości danych, oddzielając je średnikami.

   > [!NOTE]
   > Nie umieszczaj spacji między wartościami, ponieważ zakłócać w kolejności alfabetycznej na liście rozwijanej miejsc do magazynowania.

4. Kliknij przycisk **Enter** po zakończeniu dodawania wartości.

Aby uzyskać informacje na powiększanie część rozwijana pola kombi, zobacz [ustawianie rozmiaru pola kombi i jego listy rozwijanej](setting-the-size-of-the-combo-box-and-its-drop-down-list.md).

> [!NOTE]
> Nie można dodać wartości do projektów Win32 przy użyciu tej procedury ( **danych** właściwość jest wyszarzona dla projektów Win32). Ponieważ projekty Win32 nie ma bibliotek, które dodania tej możliwości, należy dodać wartości do pola kombi w projekcie systemu Win32 programowo.

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>Aby przetestować wyświetlania wartości w polu kombi

1. Po wprowadzeniu wartości w **danych** właściwości, kliknij przycisk **testu** znajdujący się na [paska narzędzi edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

   Wypróbuj, przewijając w dół listę całej wartości. Wartości wyświetlane dokładnie tak, jak są wpisywane **danych** właściwość **właściwości** okna. Nie ma pisowni lub sprawdzanie wielkość liter.

   Naciśnij klawisz **Esc** aby powrócić do **okno dialogowe** edytora.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)