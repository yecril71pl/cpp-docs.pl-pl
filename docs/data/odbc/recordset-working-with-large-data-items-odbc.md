---
title: 'Zestaw rekordów: Praca z dużymi elementami danych (ODBC) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BLOB (binary large object), recordsets
- ODBC recordsets, binary large objects
- recordsets, binary large objects
- binary large objects
- CLongBinary class, using in recordsets
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 315ebca00b42f868a5321e206591ef346804f7b6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50082453"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>Zestaw rekordów: praca z dużymi elementami danych (ODBC)

Ten temat dotyczy klas MFC DAO i klasach MFC ODBC.

> [!NOTE]
>  Jeśli używasz klas MFC DAO zarządzanie z dużymi elementami danych za pomocą klasy [CByteArray](../../mfc/reference/cbytearray-class.md) zamiast klasy [CLongBinary](../../mfc/reference/clongbinary-class.md). Jeśli za pomocą klas MFC ODBC zbiorcze pobieranie z wiersza, użyj `CLongBinary` zamiast `CByteArray`. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Załóżmy, że bazy danych można przechowywać dużych fragmentów danych, takie jak mapy bitowe (zdjęcia pracowników, mapy, obrazy produktów, obiekty OLE i tak dalej). Tego rodzaju danych jest często określane jako duży obiekt binarny (lub obiektów BLOB) ponieważ:

- Każda wartość pola jest duży.

- W odróżnieniu od liczb i innych typów prostych danych ma rozmiar nie przewidywalne.

- Dane są formless z perspektywy programu.

W tym temacie wyjaśniono, jaka pomoc techniczna klasy bazy danych zapewnia do pracy z takich obiektów.

##  <a name="_core_managing_large_objects"></a> Zarządzanie dużych obiektów

Zestawy rekordów ma dwa sposoby rozwiązania specjalne trudności z zarządzaniem duże obiekty binarne. Można użyć klasy [CByteArray](../../mfc/reference/cbytearray-class.md) lub można użyć klasy [CLongBinary](../../mfc/reference/clongbinary-class.md). Ogólnie rzecz biorąc `CByteArray` jest preferowanym sposobem zarządzania dużych danych binarnych.

`CByteArray` wymaga większe obciążenie niż `CLongBinary` , ale może stosować bardziej, zgodnie z opisem w [klasa CByteArray](#_core_the_cbytearray_class). `CLongBinary` opisano skrótowo w [klasa CLongBinary](#_core_the_clongbinary_class).

Aby uzyskać szczegółowe informacje o używaniu `CByteArray` do pracy z dużymi elementami danych, zobacz [techniczne 45 Uwaga](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

##  <a name="_core_the_cbytearray_class"></a> Klasa CByteArray

`CByteArray` jest jednym z klasy kolekcji MFC. A `CByteArray` obiekt przechowuje dynamiczne tablice bajtów — tablicy można powiększać w razie potrzeby. Klasy zapewnia szybki dostęp przez indeks, podobnie jak w przypadku wbudowanych tablic C++. `CByteArray` obiekty można serializować i zrzucone do celów diagnostycznych. Klasa dostarcza funkcji elementów członkowskich do pobierania i ustawienie określonych bajtów, wstawianie dołączanie bajtów i usunięcie jednego bajtu lub wszystkie wartości bajtowe. Tych urządzeń upewnij się, analizowanie danych binarnych łatwiejsze. Na przykład jeśli obiekt binarny jest obiekt OLE, może być konieczne trzymać się kolejności bajtów niektóre nagłówka, aby dotrzeć do rzeczywistego obiektu.

##  <a name="_core_using_cbytearray_in_recordsets"></a> Używanie CByteArray w zestawach rekordów

Dając element członkowski danych pola zestawu rekordów typu `CByteArray`, zapewnienia stałej podstawowy, z którego [RFX](../../data/odbc/record-field-exchange-rfx.md) można zarządzać transferem takiego obiektu między rekordów a źródłem danych oraz za pomocą którego można manipulować dane wewnątrz obiektu. RFX wymaga określonej witryny na potrzeby pobrane dane i potrzebny możliwość dostępu do danych bazowych.

Aby uzyskać szczegółowe informacje o używaniu `CByteArray` do pracy z dużymi elementami danych, zobacz [techniczne 45 Uwaga](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

##  <a name="_core_the_clongbinary_class"></a> Clongbinary — klasa

A [CLongBinary](../../mfc/reference/clongbinary-class.md) obiekt jest prostą powłoki wokół `HGLOBAL` obsługi blok pamięci przydzielony na stosie. Gdy powiąże kolumnie tabeli zawierającej duży obiekt binarny, przydziela RFX `HGLOBAL` obsługi, gdy trzeba przenieść dane do zestawu rekordów i przechowuje dojście w `CLongBinary` pole zestawu rekordów.

Z kolei używasz `HGLOBAL` obsłużyć, `m_hData`, aby pracować z danymi, działających na nim, jak będzie na dowolnym obsługi danych. Jest to miejsce [CByteArray](../../mfc/reference/cbytearray-class.md) dodaje możliwości.

> [!CAUTION]
>  Obiekty clongbinary — nie można użyć jako parametrów w wywołaniach funkcji. Ponadto, ich wdrażania, która wywołuje `::SQLGetData`, niekoniecznie zmniejsza wydajność przewijany migawki. To może również być spełnione, gdy używasz `::SQLGetData` wywołać sobie, aby pobrać schemat dynamiczny kolumn.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: uzyskiwanie sum i innych wyników agregacji (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)