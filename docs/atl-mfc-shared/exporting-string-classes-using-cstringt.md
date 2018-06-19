---
title: Eksportowanie klas ciągu przy użyciu CStringT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CStringT class, exporting strings
ms.assetid: bdfc441e-8d2a-461c-9885-46178066c09f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7510b1f44f49d17211c71419f4dde5a6e6a78974
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356399"
---
# <a name="exporting-string-classes-using-cstringt"></a>Eksportowanie klas ciągu przy użyciu CStringT
W przeszłości deweloperzy MFC ma pochodzi od `CString` do specialize własnych klas ciągu. W programie Microsoft Visual C++ .NET (MFC 8.0) [cstring —](../atl-mfc-shared/using-cstring.md) klasy został zastąpiony przez szablon klasy o nazwie [CStringT](../atl-mfc-shared/reference/cstringt-class.md). Ta udostępniona kilka korzyści:  
  
-   Dozwolone MFC `CString` klasy do użycia w ATL projektów bez konsolidacji w większych biblioteki DLL lub biblioteką statyczną MFC.  
  
-   Z nowym `CStringT` klasy szablonu można dostosować `CString` zachowanie przy użyciu parametrów szablonu, które określają cech znaków, podobnie jak szablony w standardowa biblioteka C++.  
  
-   Podczas eksportowania klasy ciągu z biblioteki DLL przy użyciu `CStringT`, kompilator automatycznie eksportuje `CString` klasy podstawowej. Ponieważ `CString` jest klasą szablonu go może zostać zrealizowane przez kompilator, gdy jest używany, chyba że zna kompilator który `CString` jest zaimportowany z biblioteki DLL. W przypadku migracji projektów programu Visual C++ 6.0 do programu Visual C++ .NET, może być przejrzane błędy konsolidatora symbol dla wielokrotnie zdefiniowane przez `CString` z powodu kolizji z `CString` zaimportowany z biblioteki DLL i wersji lokalnie skonkretyzowanym. Poniżej opisano właściwy sposób, aby to zrobić. Aby uzyskać więcej informacji na ten problem, zobacz artykuł bazy wiedzy, "łączenie błędy podczas importowania pochodnych cstring — klas" (Q309801) w [ http://support.microsoft.com/default.aspx ](http://support.microsoft.com/default.aspx).  
  
 Poniższy scenariusz spowoduje, że konsolidator, aby utworzyć błędy symbol dla klas wieloma definicjami. Załóżmy, że w przypadku eksportowania `CString`-klasy (`CMyString`) z biblioteki DLL rozszerzenia MFC:  
  
 [!code-cpp[NVC_MFC_DLL#6](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_1.cpp)]  
  
 Kod klienta używa kombinację `CString` i `CMyString`. "MyString.h" nie jest objęta prekompilowanego nagłówka, a niektóre użycie `CString` nie ma `CMyString` widoczne.  
  
 Załóżmy, że `CString` i `CMyString` klasy w plikach źródłowych oddzielne, Source1.cpp i Source2.cpp. W Source1.cpp, możesz użyć `CMyString` i #include MyString.h. W Source2.cpp, możesz użyć `CString`, ale nie #include MyString.h. W takim przypadku konsolidator będzie skarżą się o `CStringT` jest zdefiniowany wiele razy. Jest to spowodowane `CString` jest zarówno zaimportowany z biblioteki DLL, które eksportuje `CMyString`i utworzone lokalnie przez kompilator za pośrednictwem `CStringT` szablonu.  
  
 Aby rozwiązać ten problem, wykonaj następujące czynności:  
  
 Eksportuj `CStringA` i `CStringW` (i niezbędne klasy podstawowej) z MFC90. BIBLIOTEKI DLL. Projekty, które obejmują MFC zawsze będzie korzystać z biblioteki DLL MFC wyeksportowane `CStringA` i `CStringW`, jak w poprzednich implementacjach MFC.  
  
 Następnie utwórz można eksportować klasy pochodnej przy użyciu `CStringT` szablonu, jako `CStringT_Exported` znajduje się poniżej, na przykład:  
  
 [!code-cpp[NVC_MFC_DLL#7](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_2.cpp)]  
  
 W AfxStr.h, Zastąp poprzedniej `CString`, `CStringA`, i `CStringW` definicje typów w następujący sposób:  
  
 [!code-cpp[NVC_MFC_DLL#8](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_3.cpp)]  
  
 Istnieje kilka ostrzeżenia:  
  
-   Nie należy wyeksportować `CStringT` się, ponieważ spowoduje to ATL — tylko do projektów wyeksportować specjalistycznej `CStringT` klasy.  
  
-   Za pomocą można eksportować pochodnej klasy z `CStringT` minimalizuje konieczność ponownego zaimplementowania `CStringT` funkcji. Dodatkowy kod jest ograniczona do przekazywania konstruktorów `CStringT` klasy podstawowej.  
  
-   `CString`, `CStringA`, i `CStringW` tylko powinna być oznaczona jako `__declspec(dllexport/dllimport)` gdy tworzysz z MFC współdzielonej biblioteki DLL. Jeśli połączenie z biblioteką statyczną MFC, należy nie oznaczyć te klasy eksportowanie; użycie, w przeciwnym razie wewnętrzny `CString`, `CStringA`, i `CStringW` wewnątrz oznaczy użytkownika biblioteki dll `CString` jak również wyeksportować.  
  
## <a name="related-topics"></a>Tematy pokrewne  
 [CStringT, klasa](../atl-mfc-shared/reference/cstringt-class.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przy użyciu CStringT](../atl-mfc-shared/using-cstringt.md)   
 [Użycie CString](../atl-mfc-shared/using-cstring.md)

