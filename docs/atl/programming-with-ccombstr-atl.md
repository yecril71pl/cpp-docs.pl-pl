---
title: Programowanie przy użyciu CComBSTR (ALT)
ms.date: 11/04/2016
helpviewer_keywords:
- CComBSTR class, programming with
- Unicode, using CComBSTR [ATL]
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
ms.openlocfilehash: 806d23730a0657fc1e0c154e20dc9abd62f7e8af
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259415"
---
# <a name="programming-with-ccombstr-atl"></a>Programowanie przy użyciu CComBSTR (ALT)

Klasy ATL [CComBSTR](../atl/reference/ccombstr-class.md) stanowi otokę typ danych. Gdy `CComBSTR` stanowi przydatne narzędzie, istnieje kilka sytuacji, które wymagają Uwaga.

- [Problemy przy konwersji](#programmingwithccombstr_conversionissues)

- [Problemy z zakresu](#programmingwithccombstr_scopeissues)

- [Zwalnianie jawne obiektu CComBSTR](#programmingwithccombstr_explicitlyfreeing)

- [Przy użyciu CComBSTR obiektów w pętli](#programmingwithccombstr_usingloops)

- [Problemy z przeciek pamięci](#programmingwithccombstr_memoryleaks)

##  <a name="programmingwithccombstr_conversionissues"></a> Problemy przy konwersji

Chociaż kilka `CComBSTR` metody zostaną automatycznie przekonwertowane na zestaw Unicode argument ciąg ANSI, metody zawsze zwróci ciągów formatu Unicode. Aby przekonwertować ciąg wyjściowy ANSI, należy użyć klasy ATL konwersji. Aby uzyskać więcej informacji na temat klasy konwersji ATL, zobacz [ATL i makr konwersji ciągu MFC](reference/string-conversion-macros.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/cpp/programming-with-ccombstr-atl_1.cpp)]

Jeśli używasz literału ciągu do modyfikowania `CComBSTR` obiektu, należy użyć ciągów znaków dwubajtowych. Zmniejszy to niepotrzebnych konwersji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/cpp/programming-with-ccombstr-atl_2.cpp)]

##  <a name="programmingwithccombstr_scopeissues"></a> Problemy z zakresu

Podobnie jak w przypadku każdej dobrze behaved klasy `CComBSTR` spowoduje zwolnienie zasobów, gdy go wykracza poza zakres. Jeśli funkcja zwraca wskaźnik do `CComBSTR` ciągu, może to powodować problemy, ponieważ wskaźnik będzie odwoływać się do pamięci, który został już zwolniony z pamięci. W takich przypadkach należy użyć `Copy` metody, jak pokazano poniżej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/cpp/programming-with-ccombstr-atl_3.cpp)]

##  <a name="programmingwithccombstr_explicitlyfreeing"></a> Zwalnianie jawne obiektu CComBSTR

Można jawnie zwolnić ciąg znajdujący się w `CComBSTR` obiektu, zanim obiekt trafia zakresu. Jeśli ciąg zostanie zwolniony, `CComBSTR` obiekt jest nieprawidłowy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/cpp/programming-with-ccombstr-atl_4.cpp)]

##  <a name="programmingwithccombstr_usingloops"></a> Przy użyciu CComBSTR obiektów w pętli

Jako `CComBSTR` klasy przydziela bufor wykonywania pewnych operacji, takich jak `+=` operatora lub `Append` metody, nie zaleca się wykonanie manipulowanie ciągami wewnątrz pętli. W takich sytuacjach `CStringT` zapewnia lepszą wydajność.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/cpp/programming-with-ccombstr-atl_5.cpp)]

##  <a name="programmingwithccombstr_memoryleaks"></a> Problemy z przeciek pamięci

Przekazywanie adresu zainicjowane `CComBSTR` działanie jako **[out]** parametru powoduje, że przeciek pamięci.

W poniższym przykładzie ciąg jest przeznaczona do przechowywania ciągu `"Initialized"` przeciek kiedy funkcja `MyGoodFunction` zamienia ciąg.

[!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/cpp/programming-with-ccombstr-atl_6.cpp)]

Aby uniknąć przecieku, należy wywołać `Empty` metody na istniejących `CComBSTR` obiektów przed przekazaniem jako adres **[out]** parametru.

Należy pamiętać, że ten sam kod nie mogłoby spowodować przeciek, jeśli parametr funkcji **[w, zewnętrzne]**.

## <a name="see-also"></a>Zobacz także

[Pojęcia](../atl/active-template-library-atl-concepts.md)<br/>
[CStringT, klasa](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[wstring](../standard-library/basic-string-class.md)<br/>
[Makra konwersji ciągów](../atl/reference/string-conversion-macros.md)
