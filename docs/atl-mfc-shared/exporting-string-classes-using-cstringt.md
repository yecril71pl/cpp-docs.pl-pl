---
title: Eksportowanie klas ciągów przy użyciu CStringT | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5355b6e81354ef04b7cc4d2c3495289c9d1d029d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444208"
---
# <a name="exporting-string-classes-using-cstringt"></a>Eksportowanie klas ciągów przy użyciu CStringT

W przeszłości deweloperzy MFC mają pochodną `CString` specjalizacja własnych klas ciągów. W programie Microsoft Visual C++ .NET (MFC 8.0) [CString](../atl-mfc-shared/using-cstring.md) klasa została zastąpiona przez klasę szablonu o nazwie [CStringT](../atl-mfc-shared/reference/cstringt-class.md). Dostępne to kilka korzyści:

- Dozwolone MFC `CString` klasy, które zostaną użyte w ATL projektów bez konsolidacji w większych MFC biblioteki statycznej lub DLL.

- Przy użyciu nowego `CStringT` klasy szablonu, można dostosować `CString` zachowanie za pomocą parametrów szablonu, określających cech, podobne do szablonów w standardowej biblioteki języka C++.

- Podczas eksportowania klasy ciągu z biblioteki DLL za pomocą `CStringT`, kompilator automatycznie eksportuje `CString` klasy bazowej. Ponieważ `CString` sama jest klasą szablonu, jego mogą być tworzone przez kompilator, gdy jest używana, chyba że kompilator zdaje sobie sprawę, `CString` została zaimportowana z biblioteki DLL. Po przeprowadzeniu migracji projektów z Visual C++ 6.0 do programu Visual C++ .NET, możesz już znać konsolidatora symbol błędy mnożenia zdefiniowanych `CString` ze względu na konflikt z `CString` zaimportowany z biblioteki DLL i wersji lokalnie wystąpień. Poniżej opisano właściwy sposób, aby to zrobić. Aby uzyskać więcej informacji na temat tego problemu, zobacz artykuł bazy wiedzy, "łączenie błędy podczas importowania CString klasy pochodnej klasy" (Q309801) na [ http://support.microsoft.com/default.aspx ](http://support.microsoft.com/default.aspx).

Poniższy scenariusz spowoduje, że konsolidator generuje błędy symboli dla klas definicjami. Przyjęto założenie, że w przypadku eksportowania `CString`-klasy pochodnej (`CMyString`) z biblioteki DLL rozszerzenia MFC:

[!code-cpp[NVC_MFC_DLL#6](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_1.cpp)]

Kod konsumenta używa kombinacji `CString` i `CMyString`. "MyString.h" nie jest objęta prekompilowany plik nagłówkowy i niektóre użycie `CString` nie ma `CMyString` widoczne.

Załóżmy, że `CString` i `CMyString` klas w oddzielnych plikach źródłowych, Source1.cpp i Source2.cpp. W Source1.cpp, użyjesz `CMyString` i #include MyString.h. W Source2.cpp, użyjesz `CString`, ale nie #include MyString.h. W tym przypadku konsolidator będzie zgłaszać błąd `CStringT` jest zdefiniowany wielokrotnie. Jest to spowodowane `CString` jest zarówno zaimportowany z biblioteki DLL, które eksportuje `CMyString`i uruchomiony lokalnie, za pomocą kompilatora za pośrednictwem `CStringT` szablonu.

Aby rozwiązać ten problem, wykonaj następujące czynności:

Eksportuj `CStringA` i `CStringW` (i niezbędne klasy bazowej) z MFC90. BIBLIOTEKI DLL. Projekty, które obejmują MFC zawsze będzie korzystać z biblioteki MFC DLL wyeksportowane `CStringA` i `CStringW`, jak w poprzednich implementacjach MFC.

Następnie utwórz eksportowalny klasy pochodnej, w którym używana jest `CStringT` szablonu jako `CStringT_Exported` znajduje się poniżej, na przykład:

[!code-cpp[NVC_MFC_DLL#7](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_2.cpp)]

W AfxStr.h, zastąpić poprzedni `CString`, `CStringA`, i `CStringW` definicje typów w następujący sposób:

[!code-cpp[NVC_MFC_DLL#8](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_3.cpp)]

Istnieje kilka ostrzeżenia:

- Nie należy eksportować `CStringT` sam ponieważ spowoduje to projekty tylko do biblioteki ATL wyeksportować wyspecjalizowanego `CStringT` klasy.

- Za pomocą eksportowalny pochodnej klasy z `CStringT` minimalizuje mających potrzebę ponownego zaimplementowania `CStringT` funkcji. Dodatkowy kod jest ograniczona do przesyłania dalej z konstruktorów mają być `CStringT` klasy bazowej.

- `CString`, `CStringA`, i `CStringW` tylko powinna być oznaczona jako `__declspec(dllexport/dllimport)` podczas kompilowania z MFC udostępnionych bibliotek DLL. W przypadku łączenia się z biblioteki statycznej biblioteki MFC, należy nie oznaczyć tych klas jako wyeksportowane; użycie, w przeciwnym razie wewnętrznego `CString`, `CStringA`, i `CStringW` wewnątrz biblioteki DLL użytkownika spowoduje oznaczenie `CString` jak również wyeksportować.

## <a name="related-topics"></a>Tematy pokrewne

[CStringT, klasa](../atl-mfc-shared/reference/cstringt-class.md)

## <a name="see-also"></a>Zobacz też

[Użycie CStringT](../atl-mfc-shared/using-cstringt.md)<br/>
[Użycie CString](../atl-mfc-shared/using-cstring.md)

