---
title: Implementacja elementu niestandardowego Menedżera ciągów (zaawansowane metody) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 4d72ce586c7c93f6bd5ade613ab2807398a13ab7
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882159"
---
# <a name="implementation-of-a-custom-string-manager-advanced-method"></a>Implementacja elementu niestandardowego Menedżera ciągów (metoda zaawansowana)
W sytuacjach, specjalne można zaimplementować Menedżera niestandardowy ciąg, który zmienia więcej niż tylko sterty, który służy do przydzielania pamięci. W takiej sytuacji należy ręcznie zaimplementować [IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md) interfejsu Menedżera niestandardowy ciąg.  
  
 Aby to zrobić, należy najpierw zrozumieć jak [CStringT](../atl-mfc-shared/reference/cstringt-class.md) używa interfejsu do zarządzania jej danych ciągu. Każde wystąpienie `CStringT` zawiera wskaźnik do [CStringData](../atl-mfc-shared/reference/cstringdata-class.md) struktury. Ta struktura o zmiennej długości zawiera ważne informacje na temat parametrów (na przykład długość) oraz dane rzeczywiste znaków ciągu. Każdy Menedżer niestandardowy ciąg jest odpowiedzialny za przydzielanie i zwalnianie te struktury na żądanie `CStringT`.  
  
 `CStringData` Struktura obejmuje cztery pola:  
  
-   [pStringMgr](../atl-mfc-shared/reference/cstringdata-class.md#pstringmgr) to pole wskazuje `IAtlStringMgr` interfejs używany do zarządzania danymi tego ciągu. Gdy `CStringT` musi ponownego przydzielenia lub zwolnienia buforu ciągu wywoływanych przez nią Ponowna alokacja lub bezpłatnego metody tego interfejsu, przekazując `CStringData` strukturę jako parametr. Podczas przydzielania `CStringData` struktury w Menedżera ciągu, należy ustawić to pole, aby wskazywały do swojego przełożonego niestandardowy ciąg.  
  
-   [nDataLength](../atl-mfc-shared/reference/cstringdata-class.md#ndatalength) to pole zawiera Bieżąca długość logiczne ciągu przechowywane w buforze, z wyłączeniem zakończenia o wartości null. `CStringT` aktualizuje zawartość tego pola podczas zmiany długości ciągu. Podczas przydzielania `CStringData` struktury, Menedżer ciąg należy ustawić to pole do zera. Gdy ponowne przydzielanie `CStringData` struktury, Menedżer niestandardowy ciąg to pole powinno pozostać bez zmian.  
  
-   [nAllocLength](../atl-mfc-shared/reference/cstringdata-class.md#nalloclength) to pole zawiera maksymalną liczbę znaków (z wyjątkiem kończącego null), które mogą być przechowywane w tym buforu ciągu bez relokacja go. Zawsze, gdy `CStringT` trzeba zwiększyć logiczne długość ciągu, najpierw sprawdza on, to pole, aby upewnić się, że istnieje wystarczająca ilość miejsca w buforze. W przypadku niepowodzenia sprawdzania `CStringT` wywołania do swojego przełożonego niestandardowy ciąg ponownie przydzielić buforu. Podczas przydzielania lub relokacja `CStringData` struktury, należy ustawić to pole do liczbę znaków wymaganą w *nChars* parametr [IAtlStringMgr::Allocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#allocate) lub [IAtlStringMgr::Reallocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate). Jeśli istnieje więcej miejsca w buforze niż żądana, można ustawić tę wartość, aby odzwierciedlić rzeczywistą ilość dostępnego miejsca. Dzięki temu `CStringT` rośnie ciąg do wypełnienia całego miejsca przydzielonego przed musi wywoływać Menedżera ciągów ponownie przydzielić buforu.  
  
-   [nRefs](../atl-mfc-shared/reference/cstringdata-class.md#nrefs) to pole zawiera licznik odwołań bieżącego buforu ciągu miejsca. Jeśli wartość wynosi jeden, a następnie pojedyncze wystąpienie `CStringT` używa buforu. Ponadto wystąpienie może odczytywać i modyfikować zawartość buforu. Jeśli wartość jest większa niż jeden, kilka wystąpień `CStringT` służy buforu. Ponieważ buforu znaków są dzielone, `CStringT` wystąpień może jedynie odczytywać zawartość buforu. Aby zmodyfikować zawartość, `CStringT` najpierw tworzy kopię buforu. Jeśli wartość jest liczbą ujemną, tylko jedno wystąpienie `CStringT` używa buforu. W tym przypadku jest uznawany za buforu zablokowany. Gdy `CStringT` wystąpienie jest przy użyciu zablokowane buforu nie inne wystąpienia `CStringT` może udostępniać buforu. Zamiast tego te wystąpienia Utwórz kopię buforu przed manipulowanie zawartością. Ponadto `CStringT` wystąpienia przy użyciu zablokowane bufor nie jest podejmowana próba Udostępnij bufor wszelkich innych `CStringT` wystąpienia do niej przypisany. W tym przypadku `CStringT` wystąpienia kopiuje drugi ciąg do zablokowanej buforu.  
  
     Podczas przydzielania `CStringData` struktury, należy ustawić to pole odzwierciedlające typ udostępnianie jest dozwolone dla buforu. W większości implementacji ustawić tę wartość. Dzięki temu zwykłe zachowanie udostępniania kopii przy zapisie. Jednak jeśli Menedżer ciągu nie obsługuje udostępniania buforu ciągu, Ustaw to pole stanie zablokowanym. Zmusza to `CStringT` do użycia tylko tego buforu dla wystąpienia `CStringT` który przydzielony.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią za pomocą CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

