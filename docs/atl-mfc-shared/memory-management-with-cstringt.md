---
title: "Zarządzanie pamięcią z CStringT | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringT
- ATL::CStringT
- ATL.CStringT
dev_langs: C++
helpviewer_keywords:
- CString objects, memory management
- memory [C++], usage
- IAtlStringMgr class, using
- strings [C++], custom memory management
- CFixedStringT class, description of
- strings [C++], memory management
- CStringT class, memory management
ms.assetid: 88b8342d-19b5-48c4-9cf6-e4c44cece21e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5f36e27a536ce8983baaca594b5768479b16a74d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="memory-management-with-cstringt"></a>Zarządzanie pamięcią z CStringT
Klasa [CStringT](../atl-mfc-shared/reference/cstringt-class.md) to klasa szablonu używany do manipulowania ciągów znakowych o zmiennej długości. Pamięć do przechowywania tych ciągów jest przydzielane i wydane przez obiekt menedżera ciągu skojarzone z każdym wystąpieniem klasy `CStringT`. MFC i ATL Podaj wystąpień domyślnego elementu `CStringT`o nazwie `CString`, `CStringA`, i `CStringW`, które manipulowania ciągów znaków różnych typów. Te typy znaków typu **tchar —**, `char`, i `wchar_t`odpowiednio. Te parametry domyślne typy przy użyciu Menedżera ciąg, który przydziela pamięć z stercie procesu (w ATL) lub sterty CRT (w MFC). W przypadku typowych aplikacji ten schemat alokacji pamięci jest wystarczająca. Jednak dla kodu wprowadzania znacznym użyć ciągów (lub wielowątkowe kodu), który menedżerów pamięci domyślne mogą nie działać optymalnie. W tym temacie opisano sposób zastępują domyślne zachowanie zarządzania pamięci z `CStringT`, tworzenie allocators — specjalnie zoptymalizowana pod kątem wykonywanego zadania.  
  
-   [Wdrożenia z menedżerem ciąg niestandardowy (Metoda podstawowa)](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)  
  
-   [Unikanie stos rywalizacji](../atl-mfc-shared/avoidance-of-heap-contention.md)  
  
-   [Wdrożenia z menedżerem ciąg niestandardowy (zaawansowana metoda)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)  
  
-   [CFixedStringT: Przykład z menedżerem ciąg niestandardowy](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe CustomString](../visual-cpp-samples.md)

