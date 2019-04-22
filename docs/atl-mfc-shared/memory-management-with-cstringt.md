---
title: Zarządzanie pamięcią za pomocą CStringT
ms.date: 11/04/2016
f1_keywords:
- CStringT
- ATL::CStringT
- ATL.CStringT
helpviewer_keywords:
- CString objects, memory management
- memory [C++], usage
- IAtlStringMgr class, using
- strings [C++], custom memory management
- CFixedStringT class, description of
- strings [C++], memory management
- CStringT class, memory management
ms.assetid: 88b8342d-19b5-48c4-9cf6-e4c44cece21e
ms.openlocfilehash: 8f83b088becf97ca3d8779a537e42369b4a8c832
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58768383"
---
# <a name="memory-management-with-cstringt"></a>Zarządzanie pamięcią za pomocą CStringT

Klasa [CStringT](../atl-mfc-shared/reference/cstringt-class.md) jest klasą szablonu, używane do manipulowania ciągami znaków o zmiennej długości. Pamięć do przechowywania tych ciągów jest przydzielane i wydawane za pośrednictwem obiekt menedżera parametry skojarzone z każdym wystąpieniem `CStringT`. MFC i ATL zapewniają wystąpieniami domyślne `CStringT`, co jest nazywane `CString`, `CStringA`, i `CStringW`, który manipulowania ciągami znaków różnych typów. Te typy znaków są typu TCHAR, **char**, i `wchar_t`, odpowiednio. Te domyślne typy parametrów za pomocą Menedżera ciąg, który przydziela pamięć ze sterty procesu (w ATL) lub stercie CRT (w MFC). W przypadku typowych aplikacji ten schemat alokacji pamięci jest wystarczająca. Jednak kod intensywnie korzystających z użytku ciągów (lub kod wielowątkowy), który menedżerów zarządzania pamięcią domyślne mogą nie działać optymalnie. W tym temacie opisano sposób zastąpienia domyślnej pamięci zachowanie zarządzania `CStringT`, tworzenie puli buforów specjalnie zoptymalizowana pod kątem wykonywanego zadania.

- [Wdrożenie niestandardowego menedżera ciągów (metoda podstawowa)](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)

- [Unikanie rywalizacji stert](../atl-mfc-shared/avoidance-of-heap-contention.md)

- [Wdrożenie niestandardowego menedżera ciągów (metoda zaawansowana)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)

- [CFixedStringT: Przykład niestandardowego Menedżera ciągów](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)

## <a name="see-also"></a>Zobacz także

[Przykładowe CustomString](../overview/visual-cpp-samples.md)
