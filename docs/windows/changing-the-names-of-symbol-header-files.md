---
title: "Zmienianie nazw symboli plików nagłówkowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.symbol.changing.header
dev_langs: C++
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
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d566afbea5b955024172a44309e5d00e47b6afbe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Wstępnie zdefiniowane symbole identyfikatorów](../windows/predefined-symbol-ids.md)