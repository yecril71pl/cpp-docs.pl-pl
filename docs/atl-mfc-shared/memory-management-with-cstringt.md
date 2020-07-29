---
title: Zarządzanie pamięcią za pomocą CStringT
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, memory management
- memory [C++], usage
- IAtlStringMgr class, using
- strings [C++], custom memory management
- CFixedStringT class, description of
- strings [C++], memory management
- CStringT class, memory management
ms.assetid: 88b8342d-19b5-48c4-9cf6-e4c44cece21e
ms.openlocfilehash: bf1f99b92761c84d59b6f7bfb9aef67d7e097893
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222033"
---
# <a name="memory-management-with-cstringt"></a>Zarządzanie pamięcią za pomocą CStringT

Klasa [CStringT](../atl-mfc-shared/reference/cstringt-class.md) jest klasą szablonu służącą do manipulowania ciągami znaków o zmiennej długości. Pamięć do przechowywania tych ciągów jest przydzielona i wydawana za pomocą obiektu menedżera ciągów skojarzonych z każdym wystąpieniem `CStringT` . Biblioteki MFC i ATL zapewniają domyślne wystąpienia `CStringT` , nazywane `CString` , `CStringA` i `CStringW` , które manipulują ciągami o różnych typach znaków. Te typy znaków są typu używanie TCHAR, **`char`** , i **`wchar_t`** , odpowiednio. Te domyślne typy ciągów używają menedżera ciągów, który przydziela pamięć ze sterty procesu (w ATL) lub sterty CRT (w MFC). W przypadku typowych aplikacji wystarcza ten schemat alokacji pamięci. Jednak dla kodu intensywnie korzystających z ciągów (lub kodu wielowątkowego) domyślne Menedżery pamięci mogą nie działać optymalnie. W tym temacie opisano, jak zastąpić domyślne zachowanie zarządzania pamięcią `CStringT` , tworząc przystawkę odpowiednio zoptymalizowane pod kątem zadań.

- [Implementacja niestandardowego menedżera ciągów (metoda podstawowa)](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)

- [Unikanie rywalizacji o sterty](../atl-mfc-shared/avoidance-of-heap-contention.md)

- [Implementacja niestandardowego menedżera ciągów (Metoda zaawansowana)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)

- [CFixedStringT: przykład niestandardowego menedżera ciągów](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)

## <a name="see-also"></a>Zobacz także

[Przykład CustomString](../overview/visual-cpp-samples.md)
