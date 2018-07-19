---
title: Implementacja elementu niestandardowego Menedżera ciągów (Metoda podstawowa) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c393489b8b4d0353ae37a21132f66e0618b3b794
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884587"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>Implementacja elementu niestandardowego Menedżera ciągów (Metoda podstawowa)
Najprostszym sposobem dostosować schematu alokacji pamięci dla danych string jest użycie ATL — pod warunkiem `CAtlStringMgr` klasy, ale Podaj pamięci własnych procedur alokacji. Konstruktor `CAtlStringMgr` przyjmuje jeden parametr: wskaźnik do `IAtlMemMgr` obiektu. `IAtlMemMgr` jest abstrakcyjna klasa bazowa, który zapewnia interfejs ogólny do sterty. Za pomocą `IAtlMemMgr` interfejsu `CAtlStringMgr` przydziela, przydzieli i zwalnia pamięć używana do przechowywania danych ciągu. Możesz albo Implementowanie `IAtlMemMgr` interfejs samodzielnie lub użyj jednego z pięciu klasy ATL — pod warunkiem pamięci w Menedżerze. Menedżerów zarządzania pamięcią ATL — pod warunkiem opakować po prostu istniejących urządzeń alokacji pamięci:  
  
-   [CCRTHeap](../atl/reference/ccrtheap-class.md) Opakowuje standardowego stosu CRT ([— funkcja malloc](../c-runtime-library/reference/malloc.md), [bezpłatne](../c-runtime-library/reference/free.md), i [realloc](../c-runtime-library/reference/realloc.md))  
  
-   [CWin32Heap](../atl/reference/cwin32heap-class.md) zawija uchwyt stosu Win32, za pomocą [HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597), [HeapFree](http://msdn.microsoft.com/library/windows/desktop/aa366701), i [HeapRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366704)  
  
-   [CLocalHeap](../atl/reference/clocalheap-class.md) Opakowuje interfejsów API systemu Win32: [Funkcja LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723), [LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730), i [LocalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366742)  
  
-   [CGlobalHeap](../atl/reference/cglobalheap-class.md) Opakowuje interfejsów API systemu Win32: [działanie funkcji GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574), [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579), i [GlobalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366590).  
  
-   [CComHeap](../atl/reference/ccomheap-class.md) Opakowuje interfejsów API programu przydzielania zadań COM: [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727), [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722), i [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280)  
  
 Na potrzeby zarządzania pamięcią ciąg, jest najbardziej użyteczne klasy `CWin32Heap` , ponieważ pozwala na tworzenie wielu niezależnych stosów. Na przykład jeśli chcesz korzystać z oddzielnym stosie do ciągów, można wykonaj następujące czynności:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]  
  
 Na potrzeby zarządzania pamięci dla tego menedżera ciągów prywatnej `CString` zmienną i przekazać wskaźnik do Menedżera jako parametr do `CString` Konstruktor zmiennej:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią za pomocą CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

