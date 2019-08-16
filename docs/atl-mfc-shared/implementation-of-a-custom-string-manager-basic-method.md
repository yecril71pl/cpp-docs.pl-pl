---
title: Implementacja niestandardowego menedżera ciągów (metoda podstawowa)
ms.date: 11/04/2016
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
ms.openlocfilehash: 92c1c46f5251980f9cefb55e052e9aff395e0e60
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491315"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>Implementacja niestandardowego menedżera ciągów (metoda podstawowa)

Najprostszym sposobem dostosowania schematu alokacji pamięci dla danych ciągu jest użycie klasy dostarczonej `CAtlStringMgr` ATL, ale udostępnienie własnych procedur alokacji pamięci. Konstruktor dla `CAtlStringMgr` przyjmuje jeden parametr: wskaźnik `IAtlMemMgr` do obiektu. `IAtlMemMgr`jest abstrakcyjną klasą bazową, która udostępnia interfejs ogólny do sterty. Za pomocą `CAtlStringMgr` interfejsu, przydzielenia, przydzielania i zwalniania pamięci używanej do przechowywania danych ciągu. `IAtlMemMgr` Można zaimplementować `IAtlMemMgr` interfejs samodzielnie lub użyć jednej z pięciu klas Menedżera pamięci dostarczonych przez ATL. Menedżery pamięci udostępnionej przez ATL po prostu zawijają istniejące obiekty alokacji pamięci:

- [CCRTHeap](../atl/reference/ccrtheap-class.md) Zawija standardowe funkcje sterty CRT ([malloc](../c-runtime-library/reference/malloc.md), [bezpłatna](../c-runtime-library/reference/free.md)i realloc [](../c-runtime-library/reference/realloc.md))

- [CWin32Heap](../atl/reference/cwin32heap-class.md) Zawija dojście sterty Win32 przy użyciu [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc), [HeapFree](/windows/win32/api/heapapi/nf-heapapi-heapfree)i [HeapRealloc](/windows/win32/api/heapapi/nf-heapapi-heaprealloc)

- [CLocalHeap](../atl/reference/clocalheap-class.md) Zawija interfejsy API Win32: [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc), [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree)i [LocalRealloc](/windows/win32/api/winbase/nf-winbase-localrealloc)

- [CGlobalHeap](../atl/reference/cglobalheap-class.md) Zawija interfejsy API Win32: [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc), [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree)i [GlobalRealloc](/windows/win32/api/winbase/nf-winbase-globalrealloc).

- [CComHeap](../atl/reference/ccomheap-class.md) Zawija interfejsy API programu przydzielania zadań COM: [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc), [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree)i [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc)

Na potrzeby zarządzania pamięcią ciągów najbardziej przydatną klasą jest `CWin32Heap` , ponieważ umożliwia tworzenie wielu niezależnych stert. Jeśli na przykład chcesz użyć oddzielnego sterty tylko dla ciągów, możesz wykonać następujące czynności:

[!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]

Aby użyć tego prywatnego Menedżera ciągów do zarządzania pamięcią dla `CString` zmiennej, Przekaż wskaźnik do Menedżera jako parametr `CString` do konstruktora zmiennej:

[!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]

## <a name="see-also"></a>Zobacz także

[Zarządzanie pamięcią za pomocą CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)
