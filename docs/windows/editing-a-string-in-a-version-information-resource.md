---
title: Edytowanie ciągu w zasobach informacji o wersji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version
dev_langs:
- C++
helpviewer_keywords:
- version information resources
- resources [Visual Studio], editing version information
ms.assetid: d3a7d4e4-7d31-47c2-902c-f50b8404ba4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 80795f912ab41809b19e77bd33f56243541d4de1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882887"
---
# <a name="editing-a-string-in-a-version-information-resource"></a>Edytowanie ciągu w zasobach informacji o wersji
### <a name="to-edit-a-string-in-a-version-information-resource"></a>Aby edytować ciągu w zasobach informacji o wersji  
  
1.  Kliknij raz element następnie ponownie wybierz go, aby rozpocząć edycji. Wprowadź zmiany bezpośrednio w tabeli informacje o wersji lub w [okna właściwości](/visualstudio/ide/reference/properties-window). Wprowadzone zmiany zostaną odzwierciedlone w obu miejscach.  
  
     **Uwaga** podczas edytowania **FILEFLAGS** klucza w edytorze informacje o wersji, można zauważyć, nie można ustawić **debugowania**, **kompilacja prywatna**, lub **Specjalne kompilacji** właściwości .RC — pliki (w oknie właściwości):  
  
    -   Ustawia Edytor informacje o wersji **debugowania** na podstawie właściwości o #ifdef skryptu zasobu **_DEBUG** kompilacji flagi.  
  
    -   Jeśli **kompilacja prywatna** klucz ma **wartość** zestawu w tabeli informacje o wersji odpowiadającego **kompilacja prywatna** właściwości (w oknie właściwości) **FILEFLAGS** klucz będzie **True**. Jeśli **wartość** jest pusta, właściwość będzie **False**. Podobnie **specjalne kompilacji** klucz (tabeli informacje o wersji) jest powiązany z **specjalne kompilacji** właściwość **FILEFLAGS** klucza.  
  
 Sekwencja informacji bloku ciągu można sortować, klikając klucz lub wartość nagłówki kolumn. Te pozycje rozmieszczanie automatycznie informacje w wybranej sekwencji.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 **Wymagania**  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor informacji o wersji](../windows/version-information-editor.md)   
 [Informacje o wersji (system Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)

