---
title: Programowanie przy użyciu CComBSTR (ALT)
ms.date: 11/04/2016
helpviewer_keywords:
- CComBSTR class, programming with
- Unicode, using CComBSTR [ATL]
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
ms.openlocfilehash: 020c2d18c721e658d15bb1451039154ae50b99f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321795"
---
# <a name="programming-with-ccombstr-atl"></a>Programowanie przy użyciu CComBSTR (ALT)

Klasa ATL [CComBSTR](../atl/reference/ccombstr-class.md) udostępnia otokę wokół typu danych BSTR. Chociaż `CComBSTR` jest użytecznym narzędziem, istnieje kilka sytuacji, które wymagają ostrożności.

- [Problemy z konwersją](#programmingwithccombstr_conversionissues)

- [Problemy z zakresem](#programmingwithccombstr_scopeissues)

- [Jawne zwalnianie obiektu CComBSTR](#programmingwithccombstr_explicitlyfreeing)

- [Korzystanie z obiektów CComBSTR w pętlach](#programmingwithccombstr_usingloops)

- [Problemy z przeciekiem pamięci](#programmingwithccombstr_memoryleaks)

## <a name="conversion-issues"></a><a name="programmingwithccombstr_conversionissues"></a>Problemy z konwersją

Chociaż `CComBSTR` kilka metod automatycznie przekonwertuje argument ciągu ANSI do Unicode, metody zawsze zwracają ciągi formatu Unicode. Aby przekonwertować ciąg wyjściowy z powrotem na ANSI, należy użyć klasy konwersji ATL. Aby uzyskać więcej informacji na temat klas konwersji ATL, zobacz [makra konwersji ciągów ATL i MFC](reference/string-conversion-macros.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/cpp/programming-with-ccombstr-atl_1.cpp)]

Jeśli używasz literału ciągu `CComBSTR` do modyfikowania obiektu, użyj ciągów znaków szerokich. Zmniejszy to niepotrzebne konwersje.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/cpp/programming-with-ccombstr-atl_2.cpp)]

## <a name="scope-issues"></a><a name="programmingwithccombstr_scopeissues"></a>Problemy z zakresem

Podobnie jak w przypadku każdej `CComBSTR` dobrze zachowanej klasy, uwolni swoje zasoby, gdy wyjdzie poza zakres. Jeśli funkcja zwraca wskaźnik `CComBSTR` do ciągu, może to spowodować problemy, jak wskaźnik będzie odwoływać się do pamięci, która została już zwolniona. W takich przypadkach `Copy` należy użyć metody, jak pokazano poniżej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/cpp/programming-with-ccombstr-atl_3.cpp)]

## <a name="explicitly-freeing-the-ccombstr-object"></a><a name="programmingwithccombstr_explicitlyfreeing"></a>Jawne zwalnianie obiektu CComBSTR

Istnieje możliwość jawnie zwolnić ciąg zawarty `CComBSTR` w obiekcie, zanim obiekt wykracza zakres. Jeśli ciąg zostanie zwolniona, `CComBSTR` obiekt jest nieprawidłowy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/cpp/programming-with-ccombstr-atl_4.cpp)]

## <a name="using-ccombstr-objects-in-loops"></a><a name="programmingwithccombstr_usingloops"></a>Korzystanie z obiektów CComBSTR w pętlach

Ponieważ `CComBSTR` klasa przydziela bufor do wykonywania niektórych `+=` operacji, `Append` takich jak operator lub metoda, nie zaleca się wykonywania manipulacji ciągami wewnątrz wąskiej pętli. W takich `CStringT` sytuacjach zapewnia lepszą wydajność.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/cpp/programming-with-ccombstr-atl_5.cpp)]

## <a name="memory-leak-issues"></a><a name="programmingwithccombstr_memoryleaks"></a>Problemy z przeciekiem pamięci

Przekazywanie adresu zainicjowane `CComBSTR` do funkcji jako **[out]** parametr powoduje przeciek pamięci.

W poniższym przykładzie ciąg przydzielony `"Initialized"` do przechowywania `MyGoodFunction` ciągu jest przeciekły, gdy funkcja zastępuje ciąg.

[!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/cpp/programming-with-ccombstr-atl_6.cpp)]

Aby uniknąć przecieku, `Empty` wywołaj `CComBSTR` metodę na istniejących obiektach przed przekazaniem adresu jako parametru **[out].**

Należy zauważyć, że ten sam kod nie spowodowałby przecieku, jeśli parametr funkcji był **[in, out]**.

## <a name="see-also"></a>Zobacz też

[Pojęcia](../atl/active-template-library-atl-concepts.md)<br/>
[CStringT, klasa](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[wstręt](../standard-library/basic-string-class.md)<br/>
[Makra konwersji ciągów](../atl/reference/string-conversion-macros.md)
