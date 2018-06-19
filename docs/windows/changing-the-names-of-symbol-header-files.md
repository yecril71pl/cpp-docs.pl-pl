---
title: Zmienianie nazw symboli plików nagłówkowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.changing.header
dev_langs:
- C++
helpviewer_keywords:
- resource files, multiple
- Resource Includes dialog box
- symbol header files, changing names
- symbol header files
- header files, changing names
- names [C++], symbol header files
- symbols, symbol header files
- Resource.h
ms.assetid: b948284a-7899-402e-ab12-9f2c8480ca9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 953ac59958748bd58fa7e9027c595bf7905e5f27
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33864232"
---
# <a name="changing-the-names-of-symbol-header-files"></a>Zmiana nazw symboli plików nagłówkowych
Zwykle wszystkie definicje są zapisywane w Resource.h symbolu. Może jednak może być konieczna zmiana to obejmują nazwę pliku, dzięki czemu możesz na przykład pracować z więcej niż jeden plik zasobu w tym samym katalogu.  
  
### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>Aby zmienić nazwę pliku nagłówka symboli zasobów  
  
1.  W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy plik .rc i wybierz [zasobów zawiera](../windows/resource-includes-dialog-box.md) z menu skrótów.  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera już plik .rc, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).  
  
2.  W **plik nagłówka symbolu** wpisz nową nazwę dla pliku dyrektywy include.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.*  
  
 Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Wyświetlanie symboli zasobów](../windows/viewing-resource-symbols.md)   
 [Wstępnie zdefiniowane identyfikatory symboli](../windows/predefined-symbol-ids.md)