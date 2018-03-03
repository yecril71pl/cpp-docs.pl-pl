---
title: "Wdrożenia z menedżerem ciąg niestandardowy (podstawowa metoda) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b80af4fc8b463b6987f586c426bd465520f75ba6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>Wdrożenia z menedżerem ciąg niestandardowy (Metoda podstawowa)
Najprostszym sposobem dostosowania schematu alokacji pamięci dla danych dotyczących ciągu jest korzystanie z warunkiem ATL **CAtlStringMgr** klasy, ale podać własne pamięci procedury alokacji. Konstruktor **CAtlStringMgr** przyjmuje jeden parametr: wskaźnik do `IAtlMemMgr` obiektu. `IAtlMemMgr`jest to abstrakcyjna klasa podstawowa, który udostępnia interfejs rodzajowy na stos. Przy użyciu `IAtlMemMgr` interfejsu **CAtlStringMgr** przydziela ponownie i zwalnia pamięć używana do przechowywania danych ciągu. Można albo zaimplementuj `IAtlMemMgr` interfejsu użytkownika, lub użyj jednej z pięciu klasy Menedżer pamięci ATL — pod warunkiem. Menedżerowie pamięci ATL — pod warunkiem zawijać po prostu istniejących urządzeń alokacji pamięci:  
  
-   [CCRTHeap](../atl/reference/ccrtheap-class.md) Opakowuje standardowe funkcje sterty CRT ([— funkcja malloc](../c-runtime-library/reference/malloc.md), [wolnego](../c-runtime-library/reference/free.md), i [realloc](../c-runtime-library/reference/realloc.md))  
  
-   [CWin32Heap](../atl/reference/cwin32heap-class.md) zawija sterty Win32 obsługi, za pomocą [HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597), [HeapFree](http://msdn.microsoft.com/library/windows/desktop/aa366701), i [HeapRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366704)  
  
-   [CLocalHeap](../atl/reference/clocalheap-class.md) Opakowuje interfejsów API Win32: [Funkcja LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723), [LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730), i [LocalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366742)  
  
-   [CGlobalHeap](../atl/reference/cglobalheap-class.md) Opakowuje interfejsów API Win32: [działanie funkcji GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574), [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579), i [GlobalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366590).  
  
-   [CComHeap](../atl/reference/ccomheap-class.md) Opakowuje API alokatora zadań COM: [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727), [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722), i [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280)  
  
 Na potrzeby zarządzania pamięcią ciąg, jest najbardziej przydatna klasy `CWin32Heap` , ponieważ umożliwia tworzenie wielu niezależnych stosów. Na przykład jeśli chcesz używać oddzielnego sterty tylko do ciągów, można wykonaj następujące czynności:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]  
  
 Za pomocą Menedżera tego ciągu prywatnej zarządzania pamięci dla `CString` zmiennej, przekazać wskaźnika do Menedżera jako parametr `CString` Konstruktor zmiennej:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią za pomocą CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

