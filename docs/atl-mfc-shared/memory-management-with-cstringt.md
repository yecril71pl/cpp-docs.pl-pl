---
title: Zarządzanie pamięcią z CStringT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStringT
- ATL::CStringT
- ATL.CStringT
dev_langs:
- C++
helpviewer_keywords:
- CString objects, memory management
- memory [C++], usage
- IAtlStringMgr class, using
- strings [C++], custom memory management
- CFixedStringT class, description of
- strings [C++], memory management
- CStringT class, memory management
ms.assetid: 88b8342d-19b5-48c4-9cf6-e4c44cece21e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b65efd934fecdab36bfa1c0c882de1dd8862c81f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="memory-management-with-cstringt"></a>Zarządzanie pamięcią z CStringT
Klasa [CStringT](../atl-mfc-shared/reference/cstringt-class.md) to klasa szablonu używany do manipulowania ciągów znakowych o zmiennej długości. Pamięć do przechowywania tych ciągów jest przydzielane i wydane przez obiekt menedżera ciągu skojarzone z każdym wystąpieniem klasy `CStringT`. MFC i ATL Podaj wystąpień domyślnego elementu `CStringT`o nazwie `CString`, `CStringA`, i `CStringW`, które manipulowania ciągów znaków różnych typów. Te typy znaków typu **tchar —**, `char`, i `wchar_t`odpowiednio. Te parametry domyślne typy przy użyciu Menedżera ciąg, który przydziela pamięć z stercie procesu (w ATL) lub sterty CRT (w MFC). W przypadku typowych aplikacji ten schemat alokacji pamięci jest wystarczająca. Jednak dla kodu wprowadzania znacznym użyć ciągów (lub wielowątkowe kodu), który menedżerów pamięci domyślne mogą nie działać optymalnie. W tym temacie opisano sposób zastępują domyślne zachowanie zarządzania pamięci z `CStringT`, tworzenie allocators — specjalnie zoptymalizowana pod kątem wykonywanego zadania.  
  
-   [Wdrożenie niestandardowego menedżera ciągów (metoda podstawowa)](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)  
  
-   [Unikanie rywalizacji stert](../atl-mfc-shared/avoidance-of-heap-contention.md)  
  
-   [Wdrożenie niestandardowego menedżera ciągów (metoda zaawansowana)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)  
  
-   [CFixedStringT: Przykład z menedżerem ciąg niestandardowy](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe CustomString](../visual-cpp-samples.md)

