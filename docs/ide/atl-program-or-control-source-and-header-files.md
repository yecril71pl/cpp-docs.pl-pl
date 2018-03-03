---
title: "ATL Program lub źródło kontroli i pliki nagłówkowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- file types [C++], ATL source and headers
ms.assetid: cb65372f-4880-4007-b582-a52eaa568fd1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3a13a4c6ddb74a6f63b5da1171a3d4360199b508
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="atl-program-or-control-source-and-header-files"></a>Program ATL lub źródło kontroli i pliki nagłówkowe
Następujące pliki są tworzone podczas tworzenia projektu ATL w programie Visual Studio, w zależności od opcji wybranej dla projektu, który można utworzyć.  
  
 Wszystkie te pliki znajdują się w *nazwa_projektu.nazwa_modułu.nazwa_procedury* katalogu i w folderze pliki nagłówków (.h pliki) lub folderu źródłowego (plików .cpp) w Eksploratorze rozwiązań.  
  
|Nazwa pliku|Opis|  
|---------------|-----------------|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.h|Pliku dołączanego głównego zawierający definicje interfejsu C++ i deklaracje elementów zdefiniowanych w ATLSample.idl identyfikator GUID. Generowane przez MIDL podczas kompilacji.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.cpp|Plik źródłowy głównego programu. Zawiera on eksporty biblioteki DLL serwera w trakcie wykonania i stosowania `WinMain` dla serwera lokalnego. Dla usługi dodatkowo implementuje wszystkie funkcje zarządzania usługi.|  
|Resource.h|Plik nagłówka pliku zasobu.|  
|StdAfx.cpp|Zawiera pliki StdAfx.h i Atlimpl.cpp.|  
|StdAfx.h|Zawiera pliki nagłówkowe ATL.|  
  
## <a name="see-also"></a>Zobacz też  
 [Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)   
 [MFC Program lub źródło kontroli i pliki nagłówkowe](../ide/mfc-program-or-control-source-and-header-files.md)   
 [Projekty CLR](../ide/files-created-for-clr-projects.md)