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
ms.openlocfilehash: 85b087d9a94905291db951e0233ba1c55fa00e6e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210147"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>Implementacja elementu niestandardowego Menedżera ciągów (Metoda podstawowa)
Najprostszym sposobem dostosować schematu alokacji pamięci dla danych string jest użycie ATL — pod warunkiem `CAtlStringMgr` klasy, ale Podaj pamięci własnych procedur alokacji. Konstruktor `CAtlStringMgr` przyjmuje jeden parametr: wskaźnik do `IAtlMemMgr` obiektu. `IAtlMemMgr` jest abstrakcyjna klasa bazowa, który zapewnia interfejs ogólny do sterty. Za pomocą `IAtlMemMgr` interfejsu `CAtlStringMgr` przydziela, przydzieli i zwalnia pamięć używana do przechowywania danych ciągu. Możesz albo Implementowanie `IAtlMemMgr` interfejs samodzielnie lub użyj jednego z pięciu klasy ATL — pod warunkiem pamięci w Menedżerze. Menedżerów zarządzania pamięcią ATL — pod warunkiem opakować po prostu istniejących urządzeń alokacji pamięci:  
  
-   [CCRTHeap](../atl/reference/ccrtheap-class.md) Opakowuje standardowego stosu CRT ([— funkcja malloc](../c-runtime-library/reference/malloc.md), [bezpłatne](../c-runtime-library/reference/free.md), i [realloc](../c-runtime-library/reference/realloc.md))  
  
-   [CWin32Heap](../atl/reference/cwin32heap-class.md) zawija uchwyt stosu Win32, za pomocą [HeapAlloc](/windows/desktop/api/heapapi/nf-heapapi-heapalloc), [HeapFree](/windows/desktop/api/heapapi/nf-heapapi-heapfree), i [HeapRealloc](/windows/desktop/api/heapapi/nf-heapapi-heaprealloc)  
  
-   [CLocalHeap](../atl/reference/clocalheap-class.md) Opakowuje interfejsów API systemu Win32: [Funkcja LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc), [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree), i [LocalRealloc](/windows/desktop/api/winbase/nf-winbase-localrealloc)  
  
-   [CGlobalHeap](../atl/reference/cglobalheap-class.md) Opakowuje interfejsów API systemu Win32: [działanie funkcji GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc), [GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree), i [GlobalRealloc](/windows/desktop/api/winbase/nf-winbase-globalrealloc).  
  
-   [CComHeap](../atl/reference/ccomheap-class.md) Opakowuje interfejsów API programu przydzielania zadań COM: [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc), [CoTaskMemFree](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemfree), i [CoTaskMemRealloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemrealloc)  
  
 Na potrzeby zarządzania pamięcią ciąg, jest najbardziej użyteczne klasy `CWin32Heap` , ponieważ pozwala na tworzenie wielu niezależnych stosów. Na przykład jeśli chcesz korzystać z oddzielnym stosie do ciągów, można wykonaj następujące czynności:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]  
  
 Na potrzeby zarządzania pamięci dla tego menedżera ciągów prywatnej `CString` zmienną i przekazać wskaźnik do Menedżera jako parametr do `CString` Konstruktor zmiennej:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią za pomocą CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

