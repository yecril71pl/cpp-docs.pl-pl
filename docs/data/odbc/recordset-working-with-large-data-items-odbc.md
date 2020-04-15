---
title: 'Zestaw rekordów: praca z dużymi elementami danych (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- BLOB (binary large object), recordsets
- ODBC recordsets, binary large objects
- recordsets, binary large objects
- binary large objects
- CLongBinary class, using in recordsets
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
ms.openlocfilehash: 872fa7229738314b86b6ae6c0d5dc5a5562b27f1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360600"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>Zestaw rekordów: praca z dużymi elementami danych (ODBC)

Ten temat dotyczy zarówno klas Odbc MFC i klas DAO MFC.

> [!NOTE]
> Jeśli używasz klas DAO MFC, zarządzaj dużymi elementami danych za pomocą klasy [CByteArray,](../../mfc/reference/cbytearray-class.md) a nie klasy [CLongBinary](../../mfc/reference/clongbinary-class.md). Jeśli używasz klas MFC ODBC z pobieraniem `CLongBinary` wierszy `CByteArray`zbiorczych, użyj, a nie . Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [Rekord rekordów: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Załóżmy, że baza danych może przechowywać duże fragmenty danych, takie jak mapy bitowe (zdjęcia pracowników, mapy, obrazy produktów, obiekty OLE itd.). Ten rodzaj danych jest często określany jako binary large object (lub BLOB), ponieważ:

- Każda wartość pola jest duża.

- W przeciwieństwie do liczb i innych prostych typów danych, nie ma przewidywalnego rozmiaru.

- Dane są bezksztowe z punktu widzenia programu.

W tym temacie wyjaśniono, jakie wsparcie klasy bazy danych zapewniają do pracy z takimi obiektami.

## <a name="managing-large-objects"></a><a name="_core_managing_large_objects"></a>Zarządzanie dużymi obiektami

Zestawy rekordów mają dwa sposoby rozwiązania specjalnej trudności z zarządzaniem dużymi obiektami binarnymi. Można użyć klasy [CByteArray](../../mfc/reference/cbytearray-class.md) lub można użyć klasy [CLongBinary](../../mfc/reference/clongbinary-class.md). Ogólnie rzecz `CByteArray` biorąc jest preferowanym sposobem zarządzania dużymi danymi binarnymi.

`CByteArray`wymaga więcej `CLongBinary` niż napowietrznych niż, ale jest bardziej zdolny, jak opisano w [CByteArray Class](#_core_the_cbytearray_class). `CLongBinary`jest krótko opisane w [klasie CLongBinary](#_core_the_clongbinary_class).

Aby uzyskać szczegółowe `CByteArray` informacje na temat używania do pracy z dużymi elementami danych, zobacz [Uwaga techniczna 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

## <a name="cbytearray-class"></a><a name="_core_the_cbytearray_class"></a>Klasa CByteArray

`CByteArray`jest jedną z klas kolekcji MFC. Obiekt `CByteArray` przechowuje dynamiczną tablicę bajtów — tablica może rosnąć w razie potrzeby. Klasa zapewnia szybki dostęp przez indeks, podobnie jak w wbudowanych tablicach C++. `CByteArray`obiekty mogą być serializowane i po cenach dumpingowych do celów diagnostycznych. Klasa dostarcza funkcje elementu członkowskiego do uzyskiwania i ustawiania określonych bajtów, wstawiania i dołączania bajtów oraz usuwania jednego bajtu lub wszystkich bajtów. Te obiekty ułatwiają analizowanie danych binarnych. Na przykład jeśli obiekt binarny jest obiektem OLE, może być trzeba pracować przez niektóre bajty nagłówka, aby dotrzeć do rzeczywistego obiektu.

## <a name="using-cbytearray-in-recordsets"></a><a name="_core_using_cbytearray_in_recordsets"></a>Korzystanie z CByteArray w recordsets

Nadając element członkowski danych pola `CByteArray`zestawie rekordów typ , należy podać stałą bazę, z której [RFX](../../data/odbc/record-field-exchange-rfx.md) może zarządzać transferem takiego obiektu między zestawem rekordów a źródłem danych i za pomocą którego można manipulować danymi wewnątrz obiektu. RFX potrzebuje określonej lokacji do pobierania danych i potrzebujesz sposobu na dostęp do danych bazowych.

Aby uzyskać szczegółowe `CByteArray` informacje na temat używania do pracy z dużymi elementami danych, zobacz [Uwaga techniczna 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

## <a name="clongbinary-class"></a><a name="_core_the_clongbinary_class"></a>Klasa CLongBinary

A [CLongBinary](../../mfc/reference/clongbinary-class.md) obiekt jest prosta `HGLOBAL` powłoka wokół dojścia do bloku magazynu przydzielonego na stercie. Gdy wiąże kolumnę tabeli zawierającą binarny duży obiekt, RFX przydziela `HGLOBAL` dojście, gdy musi przenieść dane do zbioru rekordów i przechowuje dojście w `CLongBinary` polu zestaw rekordów.

Z kolei używasz `HGLOBAL` uchwytu, `m_hData`do pracy z samymi danymi, działając na nim tak, jak na dowolnych danych uchwytu. To jest, gdy [CByteArray](../../mfc/reference/cbytearray-class.md) dodaje możliwości.

> [!CAUTION]
> CLongBinary obiekty nie mogą być używane jako parametry w wywołaniach funkcji. Ponadto ich implementacja, `::SQLGetData`która wywołuje , koniecznie spowalnia wydajność przewijania dla przewijanej migawki. Może to być również prawdą, gdy używasz `::SQLGetData` wywołania samodzielnie do pobierania dynamicznych kolumn schematu.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: uzyskiwanie sum i innych wyników agregacji (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[Wymiana pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md)
