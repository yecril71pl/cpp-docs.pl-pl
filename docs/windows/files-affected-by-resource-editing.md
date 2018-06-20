---
title: Pliki uszkodzone przez edytowanie zasobów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/18/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resource editing
- resources [Visual Studio], editing
ms.assetid: d0820df1-ba84-40ac-bce9-29ea5ee7e3f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b165dca13e30e12e1a4fdc85056920b7c10ee586
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238659"
---
# <a name="files-affected-by-resource-editing"></a>Pliki, których dotyczy edytowanie zasobów
Środowiska Visual Studio działa pliki przedstawione w poniższej tabeli w podczas sesji edytowania zasobów.  
  
|Nazwa pliku|Opis|  
|---------------|-----------------|  
|Resource.h|Plik nagłówka wygenerowane przez środowisko deweloperskie; zawiera definicje symbolu. (Dołącz ten plik w kontroli źródła).|  
|Filename.APS|Binarna wersja bieżącego pliku skryptu zasobu; używany do szybkiego ładowania.<br /><br /> Edytory zasobów bezpośrednio odczytu nie .rc lub resource.h plików. Kompilator zasobów kompiluje je w .aps pliki, które są używane przez edytory zasobów. Ten plik jest to krok kompilacji i przechowuje dane tylko symboliczne danych. Jak w zwykłym skompilować procesu, informacje, które nie jest symboliczne (na przykład komentarzy) zostaną odrzucone podczas procesu kompilacji. Zawsze, gdy plik .aps pobiera synchronizację z plik .rc, zostanie ponownie wygenerowany plik .rc (na przykład podczas zapisywania, Edytor zasobów zastępuje plik .rc i plik resource.h). Zmiany wprowadzone w samych zasobach pozostaną dołączone w plik .rc, ale komentarze zostać utracone po plik .rc jest zastępowany. Aby uzyskać informacje na temat sposobu Zachowaj komentarze, zobacz [tym zasobów w czasie kompilowania](../windows/how-to-include-resources-at-compile-time.md). (Zazwyczaj nie należy używać pliku .aps w kontroli źródła.)|  
|.RC —|Plik skryptu zasobu, który zawiera skrypt zasobów w bieżącym projekcie. Jest on zastępowany przy użyciu pliku .aps zawsze, gdy zostanie zapisany. (Dołącz ten plik w kontroli źródła).|  
  

  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki zasobów](../windows/resource-files-visual-studio.md)