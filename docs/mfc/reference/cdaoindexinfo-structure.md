---
title: Cdaoindexinfo — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoIndexInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Indexes collection
- CDaoIndexInfo structure [MFC]
ms.assetid: 251d8285-78ce-4716-a0b3-ccc3395fc437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2cfeaada169addc01bc09893db0dedba2b7528d0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403113"
---
# <a name="cdaoindexinfo-structure"></a>CDaoIndexInfo — Struktura

`CDaoIndexInfo` Struktura zawiera informacje o obiekcie indeksu zdefiniowany dla obiektów dostępu do danych (DAO).

## <a name="syntax"></a>Składnia

```cpp
struct CDaoIndexInfo {
    CDaoIndexInfo();                    // Constructor
    CString m_strName;                  // Primary
    CDaoIndexFieldInfo* m_pFieldInfos;  // Primary
    short m_nFields;                    // Primary
    BOOL m_bPrimary;                    // Secondary
    BOOL m_bUnique;                     // Secondary
    BOOL m_bClustered;                  // Secondary
    BOOL m_bIgnoreNulls;                // Secondary
    BOOL m_bRequired;                   // Secondary
    BOOL m_bForeign;                    // Secondary
    long m_lDistinctCount;              // All

    // Below the // Implementation comment:
    // Destructor, not otherwise documented
};
```

### <a name="parameters"></a>Parametry

*m_strName*<br/>
Unikatowej nazwy obiektu pola. Aby uzyskać szczegółowe informacje zobacz temat "Nazwa właściwości" w Pomocy programu DAO.

*m_pFieldInfos*<br/>
Wskaźnik do tablicy [cdaoindexfieldinfo —](../../mfc/reference/cdaoindexfieldinfo-structure.md) obiektów wskazujące, które pola tabledef lub zestawu rekordów pola klucza w indeksie. Każdy obiekt identyfikuje jednego pola w indeksie. Indeks domyślnej kolejności jest rosnąca. Każdy indeks obiekt może mieć co najmniej jedno pole reprezentujące kluczy indeksu dla każdego rekordu. Mogą one rosnąco, malejąco, lub połączenie.

*m_nfields —*<br/>
Liczba pól, przechowywane w `m_pFieldInfos`.

*m_bPrimary*<br/>
Jeśli właściwość podstawowego ma wartość TRUE, obiekt indeksu reprezentuje podstawowy indeks. Podstawowy indeks składa się z co najmniej jednego pola, które jednoznacznie identyfikują wszystkie rekordy w tabeli w preferowanej kolejności. Ponieważ pole indeksu musi być unikatowy, właściwości Unikatowy indeks obiektu jest również ustawiona na wartość TRUE w DAO. Jeśli podstawowy indeks składa się z więcej niż jednym polu, każde pole może zawierać zduplikowanych wartości, ale każda kombinacja wartości z pola indeksowane muszą być unikatowe. Podstawowy indeks składa się z klucza tabeli i zwykle zawiera te same pola jako klucz podstawowy.

Po ustawieniu klucza podstawowego dla tabeli klucza podstawowego jest automatycznie definiowana jako podstawowy indeks dla tabeli. Aby uzyskać więcej informacji zobacz tematy "Podstawowe właściwości" i "unikatowa" w Pomocy programu DAO.

> [!NOTE]
> Może istnieć, co najwyżej jeden indeks podstawowy w tabeli.

*m_bUnique*<br/>
Wskazuje, czy obiekt indeksów reprezentuje unikatowy indeks dla tabeli. Jeśli ta właściwość ma wartość TRUE, obiekt indeksów reprezentuje indeks, który jest unikatowy. Unikatowy indeks składa się z co najmniej jednego pola, które Uporządkuj logicznie wszystkie rekordy w tabeli w kolejności unikatowy, wstępnie zdefiniowane. Jeśli indeks obejmuje jedno pole, wartości w danym polu musi być unikatowa dla całej tabeli. Jeśli indeks obejmuje więcej niż jednym polu, każde pole może zawierać zduplikowanych wartości, ale każda kombinacja wartości z pola indeksowane muszą być unikatowe.

Jeśli zarówno unikatowe, jak i podstawowe właściwości obiektu indeksu są ustawione na wartość TRUE, indeks jest unikatowy i podstawowego: unikatowo identyfikuje wszystkie rekordy w tabeli w kolejności wstępnie zdefiniowane, logiczne. Jeśli właściwość podstawowego ustawiono na wartość FALSE, indeks jest indeks pomocniczy. Indeksy pomocnicze (kluczy i nonkey) logicznie organizuje rekordy w kolejności wstępnie zdefiniowanej bez służy jako identyfikator rekordy w tabeli.

Aby uzyskać więcej informacji zobacz tematy "Podstawowe właściwości" i "unikatowa" w Pomocy programu DAO.

*m_bClustered*<br/>
Wskazuje, czy obiekt indeksów reprezentuje indeksu klastrowanego dla tabeli. Jeśli ta właściwość ma wartość TRUE, obiekt indeksów reprezentuje indeks klastrowany; w przeciwnym razie nie. Indeks klastrowany, który składa się z jednego lub więcej nonkey pól, razem wzięte Rozmieść wszystkie rekordy w tabeli w preferowanej kolejności. Dane w tabeli z indeksem klastrowanym dosłownie znajduje się w kolejności określonej przez indeks klastrowany. Indeks klastrowany zapewnia wydajny dostęp do rekordów w tabeli. Aby uzyskać więcej informacji zobacz temat "Klastrowane Property" w Pomocy programu DAO.

> [!NOTE]
> Właściwość Clustered jest ignorowana w przypadku baz danych, które używają aparatu bazy danych Microsoft Jet, ponieważ aparat bazy danych Jet nie obsługuje klastrowanych indeksów.

*m_bIgnoreNulls*<br/>
Wskazuje, czy znajdują się wpisy indeksu dla rekordów, które mają wartości Null w ich pola indeksu. Jeśli ta właściwość ma wartość TRUE, pola z wartościami Null nie masz wpisu indeksu. Aby wyszukać rekordy szybciej za pomocą pola, można zdefiniować indeks dla pola. Jeśli Zezwalaj zapisów o wartości Null w zaindeksowanego pola i oczekują wiele wpisów, aby mieć wartości Null, można ustawić właściwości IgnoreNulls dla obiektu indeksu na wartość TRUE, aby zmniejszyć ilość miejsca do magazynowania, który używa indeksu. Ustawienie właściwości IgnoreNulls i ustawienie właściwości wymagane ze sobą określają, czy rekord z wartością Null indeks ma wpis indeksu, jak pokazano w poniższej tabeli.

|IgnoreNulls|Wymagane|Wartość null, w polu indeksu|
|-----------------|--------------|-------------------------|
|True|False|Dozwolone wartości null nie dodano pozycję indeksu.|
|False|False|Dozwolone wartości null Dodano pozycję indeksu.|
|Wartość PRAWDA lub FAŁSZ|True|Wartość null nie jest dozwolona; nie dodano pozycję indeksu.|

Aby uzyskać więcej informacji zobacz temat "IgnoreNulls Property" w Pomocy programu DAO.

*m_bRequired*<br/>
Wskazuje, czy obiekt DAO indeksu wymaga wartości innej niż Null. Jeśli ta właściwość ma wartość TRUE, obiekt indeks nie zezwala na wartość Null. Aby uzyskać więcej informacji zobacz temat "Wymagana właściwość" w Pomocy programu DAO.

> [!TIP]
> Po ustawieniu tej właściwości dla obiektu indeksu DAO lub obiekt pola (zawarty w tabledef, rekordów lub obiektu querydef), ustaw ją na obiekt pola. Ważność ustawienie właściwości dla obiektu pola jest sprawdzany wcześniej obiekt indeksu.

*m_bForeign*<br/>
Wskazuje, czy obiekt indeksów reprezentuje klucza obcego w tabeli. Jeśli ta właściwość ma wartość TRUE, indeks reprezentuje klucza obcego w tabeli. Klucz obcy składa się z jednego lub więcej pól w tabeli obcego, które jednoznacznie identyfikują wiersze w tabeli podstawowej. Aparat bazy danych Microsoft Jet tworzy obiekt indeksu dla tabeli obcego i ustawia właściwość obcego, tworząc relację, która wymusza więzy integralności. Aby uzyskać więcej informacji zobacz temat "Obcego Property" w Pomocy programu DAO.

*m_lDistinctCount*<br/>
Określa liczbę unikatowych wartości obiektu indeksu, które są objęte skojarzona tabela. Sprawdź właściwości DistinctCount, aby określić liczbę unikatowych wartości lub kluczy w indeksie. Dowolny klawisz, jest liczony tylko raz, nawet jeśli może istnieć wiele wystąpień tej wartości indeksu pozwala na zduplikowane wartości. Informacje te są przydatne w aplikacjach, które próbują Optymalizowanie dostępu do danych oceny Indeks informacji. Liczba unikatowych wartości jest nazywana Kardynalność indeksu obiektu. Właściwość DistinctCount będzie zawsze odzwierciedla rzeczywistą liczbę kluczy w określonym czasie. Na przykład zmiana spowodowane wycofywania transakcji nie zostaną odzwierciedlone natychmiast we właściwości DistinctCount. Aby uzyskać więcej informacji zobacz temat "DistinctCount Property" w Pomocy programu DAO.

## <a name="remarks"></a>Uwagi

Odwołania do podstawowego, pomocniczego i wszystkie powyższe wskazują, jak informacji jest zwróconych przez `GetIndexInfo` funkcja elementu członkowskiego w klasach [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) i [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo).

Obiekty indeksu nie są reprezentowane przez klasę MFC. Zamiast tego DAO obiektów podstawowych obiektów klasy MFC [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) zawiera kolekcję obiektów indeksu o nazwie kolekcja indeksy. W ramach tych zajęć, podaj dostępu poszczególne informacje indeks do elementów członkowskich lub uzyskiwaniu dostępu do nich w całości z `CDaoIndexInfo` obiektu przez wywołanie metody `GetIndexInfo` funkcja elementu członkowskiego krawędzi zawierającego go obiektu.

`CDaoIndexInfo` Konstruktor i destruktor, aby można było poprawnie przydzielić i cofnąć jej przydział pola informacji o indeksie `m_pFieldInfos`.

Informacje o pobrane przez `GetIndexInfo` funkcja elementu członkowskiego obiektu tabledef są przechowywane w `CDaoIndexInfo` struktury. Wywołaj `GetIndexInfo` funkcji składowej typu obiektu zawierającego tabledef, w których kolekcja indeksy jest przechowywany obiekt indeksu. `CDaoIndexInfo` definiuje również `Dump` kompilacje funkcja elementu członkowskiego podczas debugowania. Możesz użyć `Dump` do porzucenia zawartość `CDaoIndexInfo` obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="see-also"></a>Zobacz także

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)
