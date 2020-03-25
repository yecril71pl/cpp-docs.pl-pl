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
ms.openlocfilehash: b84365461ce6d45fccdf1922974feff5af93f99f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212761"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>Zestaw rekordów: praca z dużymi elementami danych (ODBC)

Ten temat dotyczy zarówno klas MFC ODBC, jak i klas MFC DAO.

> [!NOTE]
>  Jeśli używasz klas MFC DAO, Zarządzaj dużymi elementami danych przy użyciu klasy [CByteArray](../../mfc/reference/cbytearray-class.md) zamiast klasy [CLongBinary](../../mfc/reference/clongbinary-class.md). Jeśli używasz klas MFC ODBC z pobraniem wierszy zbiorczych, użyj `CLongBinary`, a nie `CByteArray`. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Załóżmy, że baza danych może przechowywać duże fragmenty danych, takie jak mapy bitowe (fotografie pracowników, mapy, obrazy produktów, obiekty OLE itd.). Ten rodzaj danych jest często określany jako obiekt binarny (lub obiekt BLOB), ponieważ:

- Każda wartość pola jest duża.

- W przeciwieństwie do liczb i innych prostych typów danych, nie ma rozmiaru przewidywalnego.

- Dane są niezgodne z perspektywą programu.

W tym temacie wyjaśniono, co obsługuje Klasa bazy danych do pracy z takimi obiektami.

##  <a name="managing-large-objects"></a><a name="_core_managing_large_objects"></a>Zarządzanie dużymi obiektami

Zestawy rekordów mają dwa sposoby rozwiązywania szczególnych trudności związanych z zarządzaniem dużymi obiektami binarnymi. Można użyć klasy [CByteArray](../../mfc/reference/cbytearray-class.md) lub użyć klasy [CLongBinary](../../mfc/reference/clongbinary-class.md). Ogólnie rzecz biorąc, `CByteArray` jest preferowanym sposobem zarządzania dużymi danymi binarnymi.

`CByteArray` wymaga większego nakładu pracy niż `CLongBinary`, ale ma więcej możliwości, zgodnie z opisem w [klasie CByteArray](#_core_the_cbytearray_class). `CLongBinary` został krótko opisany w [klasie CLongBinary](#_core_the_clongbinary_class).

Aby uzyskać szczegółowe informacje na temat używania `CByteArray` do pracy z dużymi elementami danych, zobacz [Uwagi techniczne 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

##  <a name="cbytearray-class"></a><a name="_core_the_cbytearray_class"></a>Klasa CByteArray

`CByteArray` jest jedną z klas kolekcji MFC. Obiekt `CByteArray` przechowuje dynamiczną tablicę bajtów — w razie konieczności można zwiększyć tablicę. Klasa zapewnia szybki dostęp według indeksu, tak jak w przypadku wbudowanych C++ tablic. `CByteArray` obiektów można serializować i zrzucić do celów diagnostycznych. Klasa dostarcza funkcje członkowskie do pobierania i ustawiania określonych bajtów, wstawiania i dołączania bajtów oraz usuwania jednego bajtu lub wszystkich bajtów. Te obiekty umożliwiają łatwiejsze analizowanie danych binarnych. Na przykład jeśli obiekt binarny jest obiektem OLE, może być konieczne przechodzenie przez niektóre bajty nagłówka w celu uzyskania dostępu do rzeczywistego obiektu.

##  <a name="using-cbytearray-in-recordsets"></a><a name="_core_using_cbytearray_in_recordsets"></a>Używanie CByteArray w zestawach rekordów

Dostarczając element członkowski danych pola do zestawu rekordów, typ `CByteArray`, udostępniasz ustaloną podstawę, z której [RFX](../../data/odbc/record-field-exchange-rfx.md) może zarządzać transferem takiego obiektu między zestawem rekordów a źródłem danych, za pomocą którego można manipulować danymi wewnątrz obiektu. RFX potrzebuje określonej lokacji do pobierania danych i potrzebujesz dostępu do danych bazowych.

Aby uzyskać szczegółowe informacje na temat używania `CByteArray` do pracy z dużymi elementami danych, zobacz [Uwagi techniczne 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

##  <a name="clongbinary-class"></a><a name="_core_the_clongbinary_class"></a>Klasa CLongBinary

Obiekt [CLongBinary](../../mfc/reference/clongbinary-class.md) jest prostą powłoką wokół `HGLOBAL` dojściem do bloku magazynu przydzieloną na stercie. Gdy tworzy powiązanie kolumny tabeli zawierającej duży obiekt binarny, RFX przypisuje dojście `HGLOBAL`, gdy musi przesłać dane do zestawu rekordów i przechowywać uchwyt w polu `CLongBinary` zestawu rekordów.

Z kolei Użyj dojścia do `HGLOBAL`, `m_hData`, aby współdziałać z danymi, na przykład na wszystkich dowolnych danych obsługi. Jest to miejsce, w którym [CByteArray](../../mfc/reference/cbytearray-class.md) dodaje możliwości.

> [!CAUTION]
>  Nie można używać obiektów CLongBinary jako parametrów w wywołaniach funkcji. Ponadto ich implementacja, która wywołuje `::SQLGetData`, niekoniecznie obniża wydajność przewijania do przewijanej migawki. Może to również być prawdziwe, jeśli używasz wywołania `::SQLGetData`, aby pobrać dynamiczne kolumny schematu.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: uzyskiwanie sum i innych wyników agregacji (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)
