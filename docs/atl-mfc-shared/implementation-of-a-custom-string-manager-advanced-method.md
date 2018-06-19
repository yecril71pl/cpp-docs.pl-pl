---
title: Implementacja programu niestandardowy ciąg Manager (zaawansowana metoda) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: 64ab7da9-47c1-4c4a-9cd7-4cc37e7f3f57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 23798a4e3c1a5d3c46ea28dec39b37697aae640f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357818"
---
# <a name="implementation-of-a-custom-string-manager-advanced-method"></a>Wdrożenia z menedżerem ciąg niestandardowy (zaawansowana metoda)
W sytuacjach, specjalne można zaimplementować Menedżera niestandardowy ciąg, który więcej niż tylko ulega zmianie stosu, który służy do przydzielenia pamięci. W takiej sytuacji należy ręcznie zaimplementować [IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md) interfejsu Menedżera niestandardowy ciąg.  
  
 W tym celu należy najpierw zrozumieć sposób [CStringT](../atl-mfc-shared/reference/cstringt-class.md) używa interfejsu do zarządzania jego danych ciągu. Każde wystąpienie `CStringT` zawiera wskaźnik do [CStringData](../atl-mfc-shared/reference/cstringdata-class.md) struktury. Ta struktura o zmiennej długości zawiera ważne informacje dotyczące ciąg (takie jak długość) oraz danych rzeczywistych znaków ciągu. Menedżer każdy niestandardowy ciąg jest odpowiedzialny za przydzielanie i zwalnianie tych struktur na żądanie `CStringT`.  
  
 `CStringData` Struktury obejmuje cztery pola:  
  
-   [pStringMgr](../atl-mfc-shared/reference/cstringdata-class.md#pstringmgr) wskazuje to pole `IAtlStringMgr` interfejs używany do zarządzania danymi to ciąg. Gdy `CStringT` konieczne ponowne przydzielenie lub wolnego buforu ciągu wywołuje realokacja lub wolnego metody tego interfejsu przekazywanie `CStringData` struktury jako parametr. Podczas przydzielania `CStringData` struktury w ciągu menedżera, należy ustawić to pole, aby wskazywał Menedżera niestandardowy ciąg.  
  
-   [nDataLength](../atl-mfc-shared/reference/cstringdata-class.md#ndatalength) to pole zawiera logiczne Bieżąca długość ciągu przechowywane w buforze bez przerywania wartości null. `CStringT` aktualizuje zawartość tego pola, gdy zmienia się długość ciągu. Podczas przydzielania `CStringData` struktury Menedżera ciąg musi ustawić tego pola na zero. Jeśli ponowne przydzielanie `CStringData` struktury Menedżera niestandardowy ciąg to pole powinno pozostać bez zmian.  
  
-   [nAllocLength](../atl-mfc-shared/reference/cstringdata-class.md#nalloclength) to pole zawiera maksymalną liczbę znaków (bez przerywania null), które mogą być przechowywane w tym buforu ciągu bez ponowne przydzielanie go. Zawsze, gdy `CStringT` należy zwiększyć logicznej długość ciągu, najpierw sprawdza to pole, upewnij się, że istnieje wystarczająca ilość miejsca w buforze. W przypadku niepowodzenia sprawdzania `CStringT` wywołuje Menedżera niestandardowy ciąg ponownie przydzielić buforu. Podczas przydzielania lub ponowne przydzielanie `CStringData` struktury, trzeba ustawić pól do liczbę znaków wymaganą w **nChars** parametr [IAtlStringMgr::Allocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#allocate) lub [IAtlStringMgr::Reallocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate). Jeśli istnieje więcej miejsca w buforze niż żądana, możesz ustawić tę wartość, aby odzwierciedlić rzeczywista ilość dostępnego miejsca. Dzięki temu `CStringT` zwiększa ciąg w celu wypełnienia całego miejsce przydzielone przed ma do wywołania zwrotnego do Menedżera ciąg ponownie przydzielić buforu.  
  
-   [nRefs](../atl-mfc-shared/reference/cstringdata-class.md#nrefs) to pole zawiera odwołanie do bieżącego liczba buforu ciągu. Jeśli wartość to jeden, a następnie pojedyncze wystąpienie `CStringT` używa buforu. Ponadto wystąpienie może czytać i zmodyfikowania zawartości buforu. Jeśli wartość jest większa niż jeden, wiele wystąpień `CStringT` można użyć buforu. Ponieważ bufor znak jest udostępniony, `CStringT` wystąpień może odczytać tylko zawartość buforu. Aby zmodyfikować zawartość, `CStringT` najpierw tworzy kopię buforu. Jeśli wartość jest liczbą ujemną, tylko jedno wystąpienie `CStringT` używa buforu. W takim przypadku bufor jest traktowane jako zablokowany. Gdy `CStringT` wystąpienie jest przy użyciu buforu zablokowanym nie inne wystąpienia `CStringT` może udostępniać buforu. Zamiast tego wystąpienia te Utwórz kopię buforu przed rozpoczęciem zawartość. Ponadto `CStringT` wystąpienia przy użyciu zablokowanym bufor nie jest podejmowana próba udostępnianie buforu wszelkich innych `CStringT` wystąpienia przypisane do niej. W takim przypadku `CStringT` wystąpienia kopiuje inny ciąg do zablokowanej buforu.  
  
     Podczas przydzielania `CStringData` struktury, należy ustawić to pole, aby odzwierciedlić typ udostępniania jest dozwolony dla buforu. W większości implementacji wartość tę należy ustawić na jeden. Dzięki temu zwykłe zachowanie udostępniania kopii przy zapisie. Jednak jeśli Menedżera ciągu nie obsługuje udostępniania buforu ciągu, należy ustawić w tym polu w stanie zablokowanym. Dzięki temu `CStringT` do użycia tylko bufor dla wystąpienia `CStringT` przydzielone go.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią za pomocą CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

