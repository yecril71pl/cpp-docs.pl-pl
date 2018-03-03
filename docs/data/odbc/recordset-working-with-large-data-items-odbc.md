---
title: "Zestaw rekordów: Praca z dużymi elementami danych (ODBC) | Dokumentacja firmy Microsoft"
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
- BLOB (binary large object), recordsets
- ODBC recordsets, binary large objects
- recordsets, binary large objects
- binary large objects
- CLongBinary class, using in recordsets
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bf82e1fabd45e9bccd63e4ba46068b75d2c2a0a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-working-with-large-data-items-odbc"></a>Zestaw rekordów: praca z dużymi elementami danych (ODBC)
Ten temat dotyczy zarówno klasach MFC ODBC i klas MFC DAO.  
  
> [!NOTE]
>  Jeśli używasz klas MFC DAO zarządzania z dużymi elementami danych przy użyciu klasy [CByteArray](../../mfc/reference/cbytearray-class.md) zamiast klasy [clongbinary —](../../mfc/reference/clongbinary-class.md). Jeśli za pomocą klasy MFC ODBC zbiorcze pobieranie z wiersza, użyj `CLongBinary` zamiast `CByteArray`. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Załóżmy, że baza danych może przechowywać dużej części danych, takich jak map bitowych (fotografie pracownika, mapy, obrazy produktów, obiektów OLE i tak dalej). Tego rodzaju danych jest często określany jako dużego obiektu binarnego (lub obiektów BLOB) ponieważ:  
  
-   Każda wartość pola jest duży.  
  
-   W odróżnieniu od liczby i inne typy proste danych ma rozmiar nie przewidywalne.  
  
-   Dane są formless z perspektywy programu.  
  
 W tym temacie wyjaśniono, jakie pomocy technicznej Podaj klasy baz danych do pracy z takich obiektów.  
  
##  <a name="_core_managing_large_objects"></a>Zarządzanie dużych obiektów  
 Zestawy rekordów ma dwa sposoby rozwiązania specjalne trudności w zarządzaniu duże obiekty binarne. Można użyć klasy [CByteArray](../../mfc/reference/cbytearray-class.md) lub można użyć klasy [clongbinary —](../../mfc/reference/clongbinary-class.md). Ogólnie rzecz biorąc `CByteArray` jest preferowany sposób zarządzać dużych danych binarnych.  
  
 `CByteArray`wymaga więcej czynności niż `CLongBinary` , ale jest bardziej funkcją zgodnie z opisem w [klasy CByteArray](#_core_the_cbytearray_class). `CLongBinary`w krótko opisano [clongbinary — klasa](#_core_the_clongbinary_class).  
  
 Aby uzyskać szczegółowe informacje o używaniu `CByteArray` Aby pracować z dużymi elementami danych, zobacz [45 Uwaga techniczna](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).  
  
##  <a name="_core_the_cbytearray_class"></a>Klasa CByteArray  
 `CByteArray`jest jednym z klasy kolekcji MFC. A `CByteArray` obiekt przechowuje dynamiczne tablicę bajtów — tablicy można wzrostu w razie potrzeby. Klasa zapewnia szybki dostęp przez indeks, podobnie jak w przypadku wbudowanych tablic C++. `CByteArray`obiekty można serializować i utworzyć zrzutu w celach diagnostycznych. Klasa udostępnia funkcje Członkowskie pobierania i ustawiania określonych bajtów, wstawiania i dołączanie bajtów i usunięcie jednego bajtu lub wszystkich bajtów. Urządzenia te należy analizowania danych binarnych. Na przykład jeśli obiekt binarny obiektu OLE, może być konieczne przechodzenia przez niektóre bajty nagłówka do rzeczywistego obiektu.  
  
##  <a name="_core_using_cbytearray_in_recordsets"></a>Przy użyciu CByteArray w zestawach rekordów  
 Zapewniając pola danych członkiem zestawu rekordów typu `CByteArray`, podaj stałym podstawowy, z którego [RFX](../../data/odbc/record-field-exchange-rfx.md) można zarządzać transferem takiego obiektu między zestawu rekordów i źródła danych oraz za pomocą którego można manipulować dane wewnątrz obiektu. RFX wymaga określonej lokacji dla pobrane dane, a potrzebują sposobu uzyskiwania dostępu do danych podstawowych.  
  
 Aby uzyskać szczegółowe informacje o używaniu `CByteArray` Aby pracować z dużymi elementami danych, zobacz [45 Uwaga techniczna](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).  
  
##  <a name="_core_the_clongbinary_class"></a>Clongbinary — klasa  
 A [clongbinary —](../../mfc/reference/clongbinary-class.md) obiekt jest proste powłoki wokół `HGLOBAL` obsługi blok pamięci przydzielony na stosie. Podczas nawiązywania połączenia kolumnie tabeli zawierającej dużego obiektu binarnego, przydziela RFX `HGLOBAL` obsługi wymaga przeprowadzenia transferu danych do zestawu rekordów i przechowuje dojście w `CLongBinary` pole zestawu rekordów.  
  
 Z kolei, użyj `HGLOBAL` obsłużyć, `m_hData`, aby pracować z danymi, działających na nim jak będzie na dowolnym obsługi danych. Jest to, gdy [CByteArray](../../mfc/reference/cbytearray-class.md) funkcji.  
  
> [!CAUTION]
>  Clongbinary — obiekty nie mogą być używane jako parametry w wywołaniach funkcji. Ponadto ich wdrażania, która wywołuje **:: Procedura SQLGetData**, niekoniecznie spowalnia działanie przewijania przewijanego migawki. Może to również być wartość true, korzystając z **:: Procedura SQLGetData** wywołać samodzielnie można pobrać schematu dynamiczne kolumn.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Zestaw rekordów: Uzyskiwanie sum i innych wyników agregacji (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)   
 [Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)