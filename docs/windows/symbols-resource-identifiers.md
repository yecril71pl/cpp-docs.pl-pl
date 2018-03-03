---
title: "Symbole: Identyfikatory zasobów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.symbol.identifiers
dev_langs:
- C++
helpviewer_keywords:
- symbols, resource identifiers
- symbols, creating
- resource symbols
- symbols, editing
- resource editors, resource symbols
ms.assetid: 8fccc09a-0237-4a65-b9c4-57d60c59e324
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 931ec9cb5d7e756d47a24c0c2b30b8686cd0fd4c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="symbols-resource-identifiers"></a>Symbole: identyfikatory zasobów
Symbol jest identyfikator zasobu (ID), która składa się z dwóch części: ciąg tekstowy (nazwa symbolu) zamapowany na wartość całkowitą (symbol wartości). Na przykład:  
  
```  
IDC_EDITNAME = 5100  
```  
  
 Nazwy symboli najczęściej są określane jako identyfikatorów.  
  
 Symbole Podaj opisową sposób odwoływania się do zasobów i obiektów interfejsu użytkownika, zarówno w kodzie źródłowym, jak i podczas pracy z nimi w edytory zasobów. Możesz wyświetlić i manipulowania symbole w go przy użyciu wygodne miejsce [okno dialogowe symboli zasobów](../windows/viewing-resource-symbols.md).  
  
 Podczas tworzenia nowego zasobu lub obiektu zasobów [edytory zasobów](../windows/resource-editors.md) Podaj nazwę domyślną dla danego zasobu, na przykład `IDC_RADIO1`i przypisz jej wartość. Definicja name plus wartości są przechowywane w pliku Resource.h.  
  
> [!NOTE]
>  Podczas kopiowania zasobów lub obiektów zasobów z jednego pliku .rc do innego, Visual C++ może zmienić wartość symbolu lub nazwy symbolu i wartość w celu uniknięcia konfliktów z wartości w istniejącym pliku lub nazwy symbolu przekazanych zasobów.  
  
 Wraz z rozwojem aplikacji i wiedzy, co powoduje jego ilość zasobów oraz symbole. Śledzenie dużej liczby symbole rozproszone w wielu plików może być trudne. [Okno dialogowe symboli zasobów](../windows/resource-symbols-dialog-box.md) upraszcza zarządzanie symbol oferując centralnej narzędzia, za pomocą których można wykonywać następujące czynności:  
  
- [Wyświetlanie symboli zasobów](../windows/viewing-resource-symbols.md)  
  
- [Tworzenie nowych symboli](../windows/creating-new-symbols.md)  
  
- [Zmiana nieprzypisanych symboli](../windows/changing-unassigned-symbols.md)  
  
- [Usuwanie nieprzypisanych symboli](../windows/deleting-unassigned-symbols.md)  
  
- [Otwórz Edytor zasobów dla podanego symbolu](../windows/opening-the-resource-editor-for-a-given-symbol.md)  
  
- [Zmiana symbolu lub nazwy symbolu (ID)](../windows/changing-a-symbol-or-symbol-name-id.md)  
  
- [Zmiana wartości numerycznej symbolu](../windows/changing-a-symbol-s-numeric-value.md)  
  
- [Zmiana nazw symboli plików nagłówkowych](../windows/changing-the-names-of-symbol-header-files.md)  
  
- [Obejmują udostępnionych (tylko do odczytu) lub obliczonych symboli](../windows/including-shared-read-only-or-calculated-symbols.md)  
  
- [Wyświetl wstępnie zdefiniowane symbole identyfikatorów](../windows/predefined-symbol-ids.md)  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: wyszukiwanie symboli w zasobach](../windows/how-to-search-for-symbols-in-resources.md)   
 [Edytory zasobów](../windows/resource-editors.md)   
 [Pliki zasobów](../windows/resource-files-visual-studio.md)

