---
title: Zmiana nazw symboli plików nagłówkowych | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 6d1c3436190ff36724eba1601a51608371b8d0a4
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649949"
---
# <a name="changing-the-names-of-symbol-header-files"></a>Zmiana nazw symboli plików nagłówkowych
Zwykle symbol wszystkie definicje są zapisywane w `Resource.h`. Może jednak może być konieczna zmiana to zawierać nazwę pliku na przykład korzystania z więcej niż jeden plik zasobów w tym samym katalogu.  
  
### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>Aby zmienić nazwę pliku nagłówkowego symboli zasobów  
  
1.  W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy plik .rc i wybierz [zasób zawiera](../windows/resource-includes-dialog-box.md) z menu skrótów.  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).  
  
2.  W **plik nagłówka symbolu** wpisz nową nazwę dla pliku dyrektywy include.  
  
 Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*.  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Wyświetlanie symboli zasobów](../windows/viewing-resource-symbols.md)   
 [Wstępnie zdefiniowane identyfikatory symboli](../windows/predefined-symbol-ids.md)