---
title: ATL Program lub źródło kontroli i pliki nagłówkowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- file types [C++], ATL source and headers
ms.assetid: cb65372f-4880-4007-b582-a52eaa568fd1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3e8e5065cebab002e9c48aef560eb9f2feab67e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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