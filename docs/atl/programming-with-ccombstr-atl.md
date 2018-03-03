---
title: "Programowanie przy użyciu CComBSTR (ALT) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CComBSTR class, programming with
- Unicode, using CComBSTR [ATL]
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8f496dd73c2d15f8f78ddbdc205f31a8520c674
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="programming-with-ccombstr-atl"></a>Programowanie przy użyciu CComBSTR (ALT)
Klasy ATL [CComBSTR](../atl/reference/ccombstr-class.md) udostępnia otokę `BSTR` — typ danych. Gdy `CComBSTR` stanowi przydatne narzędzie jest wiele sytuacji, które wymagają ostrożność.  
  
-   [Problemy z konwersją](#programmingwithccombstr_conversionissues)  
  
-   [Problemy z zakresu](#programmingwithccombstr_scopeissues)  
  
-   [Jawne zwalnianie obiektów CComBSTR](#programmingwithccombstr_explicitlyfreeing)  
  
-   [Przy użyciu CComBSTR obiektów w pętli](#programmingwithccombstr_usingloops)  
  
-   [Problemy przecieków pamięci](#programmingwithccombstr_memoryleaks)  
  
##  <a name="programmingwithccombstr_conversionissues"></a>Problemy z konwersją  
 Mimo że kilka `CComBSTR` metody automatycznie przekonwertuje argument ciągu ANSI na Unicode, metody zawsze zwróci ciągów w formacie Unicode. Aby przekonwertować ciągu wyjściowego ANSI, należy użyć klasy konwersji ATL. Aby uzyskać więcej informacji na ATL — klasy konwersji, zobacz [ATL i makr konwersji MFC ciąg](reference/string-conversion-macros.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/cpp/programming-with-ccombstr-atl_1.cpp)]  
  
 Jeśli używasz literału ciągu do modyfikowania `CComBSTR` obiekt, należy użyć ciągów znaków dwubajtowych. Zmniejsza to niepotrzebnych konwersji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/cpp/programming-with-ccombstr-atl_2.cpp)]  
  
##  <a name="programmingwithccombstr_scopeissues"></a>Problemy z zakresu  
 Podobnie jak w przypadku każdej dobrze behaved klasy `CComBSTR` zwolni jej zasobów, gdy przechodzi ona poza zakresem. Jeśli funkcja zwraca wskaźnik do `CComBSTR` ciąg, może to powodować problemy, jako wskaźnik będzie odwoływać się do pamięci, który już został zwolniony. W takich sytuacjach należy użyć **kopiowania** metody, jak pokazano poniżej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/cpp/programming-with-ccombstr-atl_3.cpp)]  
  
##  <a name="programmingwithccombstr_explicitlyfreeing"></a>Jawne zwalnianie obiektów CComBSTR  
 Istnieje możliwość jawnie wolne ciąg znajdujący się w `CComBSTR` obiekt przed obiekt wykracza poza zakres. Jeśli ciąg zostanie zwolniona, `CComBSTR` obiektu jest nieprawidłowy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/cpp/programming-with-ccombstr-atl_4.cpp)]  
  
##  <a name="programmingwithccombstr_usingloops"></a>Przy użyciu CComBSTR obiektów w pętli  
 Jako `CComBSTR` klasy przydziela buforu w celu wykonywania pewnych operacji, takich jak `+=` operator lub **Append** metody, nie zaleca się wykonanie manipulowanie ciągami wewnątrz ścisłej pętli. W takich sytuacjach `CStringT` zapewnia lepszą wydajność.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/cpp/programming-with-ccombstr-atl_5.cpp)]  
  
##  <a name="programmingwithccombstr_memoryleaks"></a>Problemy przecieków pamięci  
 Przekazywanie adresu zainicjowane `CComBSTR` mógł działać jako **[out]** parametr powoduje, że przeciek pamięci.  
  
 W poniższym przykładzie ciąg przeznaczona do przechowywania ciąg `"Initialized"` przeciek kiedy funkcja `MyGoodFunction` zamienia ciąg.  
  
 [!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/cpp/programming-with-ccombstr-atl_6.cpp)]  
  
 Aby uniknąć systemu, należy wywołać **pusty** metody na istniejącej `CComBSTR` obiektów przed przekazaniem adresów jako **[out]** parametru.  
  
 Należy pamiętać, że ten sam kod nie może powodować przeciek, jeśli parametr funkcji **[w, limit]**.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../atl/active-template-library-atl-concepts.md)   
 [Klasa CStringT](../atl-mfc-shared/reference/cstringt-class.md)   
 [wstring](../standard-library/basic-string-class.md)   
 [Makra konwersji ciągów](../atl/reference/string-conversion-macros.md)

