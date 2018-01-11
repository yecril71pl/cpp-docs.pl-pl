---
title: "Pliki uszkodzone przez edytowanie zasobów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- resource editing
- resources [Visual Studio], editing
ms.assetid: d0820df1-ba84-40ac-bce9-29ea5ee7e3f8
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3b3a5f8c8351d7056409b0e6182862213c51381a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="files-affected-by-resource-editing"></a>Pliki, których dotyczy edytowanie zasobów
Środowiska Visual Studio działa pliki przedstawione w poniższej tabeli w podczas sesji edytowania zasobów.  
  
|Nazwa pliku|Opis|  
|---------------|-----------------|  
|Resource.h|Plik nagłówka wygenerowane przez środowisko deweloperskie; zawiera definicje symbolu.|  
|Filename.APS|Binarna wersja bieżącego pliku skryptu zasobu; używany do szybkiego ładowania.<br /><br /> Edytory zasobów bezpośrednio odczytu nie .rc lub resource.h plików. Kompilator zasobów kompiluje je w .aps pliki, które są używane przez edytory zasobów. Ten plik jest to krok kompilacji i przechowuje dane tylko symboliczne danych. Jak w zwykłym skompilować procesu, informacje, które nie jest symboliczne (na przykład komentarzy) zostaną odrzucone podczas procesu kompilacji. Zawsze, gdy plik .aps pobiera synchronizację z plik .rc, zostanie ponownie wygenerowany plik .rc (na przykład podczas zapisywania, Edytor zasobów zastępuje plik .rc i plik resource.h). Zmiany wprowadzone w samych zasobach pozostaną dołączone w plik .rc, ale komentarze zostać utracone po plik .rc jest zastępowany. Aby uzyskać informacje na temat sposobu Zachowaj komentarze, zobacz [tym zasobów w czasie kompilowania](../windows/how-to-include-resources-at-compile-time.md).|  
|.RC —|Plik skryptu zasobu, który zawiera skrypt zasobów w bieżącym projekcie. Jest on zastępowany przy użyciu pliku .aps zawsze, gdy zostanie zapisany.|  
  

  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki zasobów](../windows/resource-files-visual-studio.md)