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
- controls [Visual Studio], testing values in combo boxes
- combo boxes [C++], adding values
- combo boxes [C++], previewing values
- controls [C++], testing values in combo boxes
- Data property
- combo boxes [C++], testing values
ms.assetid: 22a78f98-fada-48b3-90d8-7fa0d8e4de51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c81e40de56970571ad78ceea86084b7ff7b82227
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="adding-values-to-a-combo-box-control"></a>Dodawanie wartości do kontrolki pola kombi
Tak długo, jak należy otworzyć edytora okien dialogowych, można dodać wartości do kontrolki pola kombi.  
  
> [!TIP]
>  Jest dobrym rozwiązaniem, aby dodać wszystkie wartości do pola kombi *przed* rozmiaru pola w edytorze okien dialogowych lub może obciąć tekst, który powinien zostać wyświetlony w formancie kombi.  
  
#### <a name="to-enter-values-into-a-combo-box-control"></a>Aby wprowadzić wartości do kontrolki pola kombi  
  
1.  Wybierz kontrolki pola kombi, klikając go.  
  
2.  W [okna właściwości](/visualstudio/ide/reference/properties-window), przewiń w dół do **danych** właściwości.  
  
    > [!NOTE]
    >  W przypadku wyświetlania właściwości pogrupowane według typu, **danych** pojawia się w **różne** właściwości.  
  
3.  Kliknij obszar wartość **danych** właściwości i wpisz wartości danych, oddzielone średnikami.  
  
    > [!NOTE]
    >  Nie należy umieszczać spacji między wartości, ponieważ spacje zakłócać w kolejności alfabetycznej na liście rozwijanej.  
  
4.  Kliknij przycisk **Enter** po zakończeniu dodawania wartości.  
  
 Aby uzyskać informacje na powiększanie część rozwijana pola kombi, zobacz [ustawienie rozmiaru pole kombi i jego listy rozwijanej](setting-the-size-of-the-combo-box-and-its-drop-down-list.md).  
  
> [!NOTE]
>  Nie można dodać wartości do projektów Win32 przy użyciu tej procedury ( **danych** właściwości jest niedostępny dla projektów Win32). Ponieważ projekt Win32 nie ma bibliotek, które dodania tej możliwości, należy dodać wartości do pola kombi z projektem Win32 programowo.  
  
#### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>Aby przetestować wyświetlania wartości w polu kombi  
  
1.  Po wprowadzeniu wartości w **danych** właściwości, kliknij przycisk **testu** znajdującego się na [paska narzędzi edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).  
  
     Spróbuj przewijania w dół listy całej wartości. Wartości są wyświetlane, dokładnie tak, jak są wpisywane **danych** właściwości w oknie właściwości. Nie jest pisowni ani kontroli wielkości liter.  
  
     Naciśnij klawisz ESC, aby powrócić do edytora — okno dialogowe.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty w oknach dialogowych](../windows/controls-in-dialog-boxes.md)   
 [Kontrolki](../mfc/controls-mfc.md)

