---
title: CDaoFieldInfo — Struktura
ms.date: 09/17/2019
f1_keywords:
- CDaoFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
ms.openlocfilehash: 9466386fefc6e5ab8fcf89bf497c1d5219e3e807
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368407"
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo — Struktura

Struktura `CDaoFieldInfo` zawiera informacje o obiekcie pola zdefiniowanym dla obiektów dostępu do danych (DAO).

DAO jest obsługiwany przez pakiet Office 2013. DAO 3.6 jest ostateczną wersją i jest uważana za przestarzałą.

## <a name="syntax"></a>Składnia

```
struct CDaoFieldInfo
{
    CString m_strName;           // Primary
    short m_nType;               // Primary
    long m_lSize;                // Primary
    long m_lAttributes;          // Primary
    short m_nOrdinalPosition;    // Secondary
    BOOL m_bRequired;            // Secondary
    BOOL m_bAllowZeroLength;     // Secondary
    long m_lCollatingOrder;      // Secondary
    CString m_strForeignName;    // Secondary
    CString m_strSourceField;    // Secondary
    CString m_strSourceTable;    // Secondary
    CString m_strValidationRule; // All
    CString m_strValidationText; // All
    CString m_strDefaultValue;   // All
};
```

#### <a name="parameters"></a>Parametry

*m_strName*<br/>
Unikatowe nazwy obiektu pola. Aby uzyskać szczegółowe informacje, zobacz temat "Właściwość nazwy" w Pomocy DAO.

*m_nType*<br/>
Wartość wskazująca typ danych pola. Aby uzyskać szczegółowe informacje, zobacz temat "Typ właściwości" w Pomocy DAO. Wartość tej właściwości może być jedną z następujących czynności:

- `dbBoolean`Tak/Nie, tak samo jak PRAWDA/FAŁSZ

- `dbByte`Bajtów

- `dbInteger`Krótki

- `dbLong`Długi

- `dbCurrency`Waluta; zobacz klasa MFC [COleCurrency](../../mfc/reference/colecurrency-class.md)

- `dbSingle`Pojedynczy

- `dbDouble`Podwójne

- `dbDate`Data/godzina; zobacz klasa MFC [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)

- `dbText`Tekst; zobacz klasa MFC [CString](../../atl-mfc-shared/reference/cstringt-class.md)

- `dbLongBinary`Długi plik binarny (obiekt OLE); można użyć klasy MFC [CByteArray](../../mfc/reference/cbytearray-class.md) zamiast `CLongBinary` klasy, ponieważ `CByteArray` jest bogatsza i łatwiejsza w użyciu.

- `dbMemo`Notatka; zobacz klasa MFC`CString`

- `dbGUID`Globalnie unikatowy identyfikator/uniwersalnie unikatowy identyfikator używany z wywołaniami procedury zdalnej. Aby uzyskać więcej informacji, zobacz temat "Typ właściwości" w Pomocy DAO.

> [!NOTE]
> Nie należy używać typów danych ciągów dla danych binarnych. Powoduje to, że dane przechodzą przez warstwę tłumaczenia Unicode/ANSI, co powoduje zwiększone obciążenie i ewentualnie nieoczekiwane tłumaczenie.

*m_lSize*<br/>
Wartość wskazująca maksymalny rozmiar obiektu pola DAO zawierającego tekst lub stały rozmiar obiektu pola zawierającego tekst lub wartości liczbowe. Aby uzyskać szczegółowe informacje, zobacz temat "Właściwość rozmiaru" w Pomocy DAO. Rozmiary mogą być jedną z następujących wartości:

|Typ|Rozmiar (bajty)|Opis|
|----------|--------------------|-----------------|
|`dbBoolean`|1 bajt|Tak/Nie (tak samo jak prawda/fałsz)|
|`dbByte`|1|Byte|
|`dbInteger`|2|Liczba całkowita|
|`dbLong`|4|Długi|
|`dbCurrency`|8|Waluta ([COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|Single|
|`dbDouble`|8|Double|
|`dbDate`|8|Data/godzina ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Tekst[(CString)](../../atl-mfc-shared/reference/cstringt-class.md)|
|`dbLongBinary`|0|Long Binary (obiekt OLE; [CByteArray](../../mfc/reference/cbytearray-class.md); zamiast `CLongBinary`)|
|`dbMemo`|0|Notatka[(CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbGUID`|16|Globalnie unikatowy identyfikator/uniwersalnie unikatowy identyfikator używany z wywołaniami procedury zdalnej.|

*m_lAttributes*<br/>
Określa właściwości obiektu pola zawartego w obiekcie tabledef, recordset, querydef lub index. Zwrócona wartość może być sumą tych stałych utworzonych za pomocą operatora C++ bitwise-OR** (&#124;): **

- `dbFixedField`Rozmiar pola jest stały (domyślnie dla pól liczbowych).

- `dbVariableField`Rozmiar pola jest zmienny (tylko pola tekstowe).

- `dbAutoIncrField`Wartość pola dla nowych rekordów jest automatycznie zwiększana do unikatowej długiej liczby całkowitej, których nie można zmienić. Obsługiwane tylko dla tabel bazy danych microsoft jet.

- `dbUpdatableField`Wartość pola można zmienić.

- `dbDescending`Pole jest sortowane w kolejności malejącej (Z - A lub 100 - 0) (dotyczy tylko obiektu pola w fields kolekcji obiektu indeksu; w MFC obiekty indeksu same znajdują się w obiektach tabledef). Jeśli ta stała zostanie pominięta, pole zostanie posortowane w kolejności rosnącej (A - Z lub 0 - 100) (domyślnie).

Podczas sprawdzania ustawienia tej właściwości, można użyć C++ bitwise-AND operatora (**&**) do testowania określonego atrybutu. Podczas ustawiania wielu atrybutów można je połączyć, łącząc odpowiednie stałe z operatorem bitowym -OR** (&#124;). ** Aby uzyskać szczegółowe informacje, zobacz temat "Właściwość atrybutów" w Pomocy DAO.

*m_nOrdinalPosition*<br/>
Wartość określająca kolejność liczbową, w jakiej ma być wyświetlane pole reprezentowane przez obiekt pola DAO względem innych pól. Tę właściwość można ustawić za pomocą [właściwości CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield). Aby uzyskać szczegółowe informacje, zobacz temat "Właściwość porządkowej" w Pomocy DAO.

*m_bRequired*<br/>
Wskazuje, czy obiekt pola DAO wymaga wartości innej niż Null. Jeśli ta właściwość ma wartość PRAWDA, pole nie zezwala na wartość Null. Jeśli wymagane jest ustawione na FAŁSZ, pole może zawierać wartości Null, a także wartości, które spełniają warunki określone przez AllowZeroLength i ValidationRule ustawienia właściwości. Aby uzyskać szczegółowe informacje, zobacz temat "Wymagana właściwość" w Pomocy DAO. Tę właściwość można ustawić dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_bAllowZeroLength*<br/>
Wskazuje, czy pusty ciąg ("") jest prawidłową wartością obiektu pola DAO o typie danych Tekst lub Notatka. Jeśli ta właściwość jest TRUE, pusty ciąg jest prawidłową wartością. Tę właściwość można ustawić na FAŁSZ, aby upewnić się, że nie można użyć pustego ciągu do ustawiania wartości pola. Aby uzyskać szczegółowe informacje, zobacz temat "AllowZeroLength Property" w Pomocy DAO. Tę właściwość można ustawić dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_lCollatingOrder*<br/>
Określa kolejność sortowania w tekście do porównywania lub sortowania ciągów. Aby uzyskać szczegółowe informacje, zobacz temat "Dostosowywanie ustawień rejestru systemu Windows w celu uzyskania dostępu do danych" w Pomocy dao. Aby uzyskać listę możliwych wartości zwracanych, zobacz `m_lCollatingOrder` element członkowski struktury [CDaoDatabaseInfo.](../../mfc/reference/cdaodatabaseinfo-structure.md) Tę właściwość można ustawić dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strForeignName*<br/>
Wartość, która w relacji określa nazwę obiektu pola DAO w tabeli obcej, która odpowiada polu w tabeli podstawowej. Aby uzyskać szczegółowe informacje, zobacz temat "ForeignName Property" w Pomocy DAO.

*m_strSourceField*<br/>
Wskazuje nazwę pola, które jest oryginalnym źródłem danych dla obiektu pola DAO zawartego przez obiekt tabledef, recordset lub querydef. Ta właściwość wskazuje oryginalną nazwę pola skojarzoną z obiektem pola. Na przykład można użyć tej właściwości do określenia oryginalnego źródła danych w polu kwerendy, którego nazwa nie jest związana z nazwą pola w tabeli podstawowej. Aby uzyskać szczegółowe informacje, zobacz temat "SourceField, SourceTable Properties" w Pomocy DAO. Tę właściwość można ustawić dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strSourceTable*<br/>
Wskazuje nazwę tabeli, która jest oryginalnym źródłem danych dla obiektu pola DAO zawartego przez obiekt tabledef, recordset lub querydef. Ta właściwość wskazuje oryginalną nazwę tabeli skojarzoną z obiektem pola. Na przykład można użyć tej właściwości do określenia oryginalnego źródła danych w polu kwerendy, którego nazwa nie jest związana z nazwą pola w tabeli podstawowej. Aby uzyskać szczegółowe informacje, zobacz temat "SourceField, SourceTable Properties" w Pomocy DAO. Tę właściwość można ustawić dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strValidationRule*<br/>
Wartość, która sprawdza poprawność danych w polu, ponieważ są zmieniane lub dodawane do tabeli. Aby uzyskać szczegółowe informacje, zobacz temat "ValidationRule Property" w Pomocy DAO. Tę właściwość można ustawić dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

Aby uzyskać powiązane informacje na `m_strValidationRule` temat tabledefs, zobacz element członkowski struktury [CDaoTableDefInfo.](../../mfc/reference/cdaotabledefinfo-structure.md)

*m_strValidationText*<br/>
Wartość określająca tekst komunikatu wyświetlanego przez aplikację, jeśli wartość obiektu pola DAO nie spełnia reguły sprawdzania poprawności określonej przez ustawienie właściwości ValidationRule. Aby uzyskać szczegółowe informacje, zobacz temat "ValidationText Property" w Pomocy DAO. Tę właściwość można ustawić dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strDefaultValue*<br/>
Wartość domyślna obiektu pola DAO. Po utworzeniu nowego rekordu ustawienie właściwości DefaultValue jest automatycznie wprowadzane jako wartość pola. Aby uzyskać szczegółowe informacje, zobacz temat "DefaultValue Property" w Pomocy DAO. Tę właściwość można ustawić dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

## <a name="remarks"></a>Uwagi

Odwołania do podstawowych, pomocniczych i wszystkie powyżej wskazują, `GetFieldInfo` jak informacje są zwracane przez funkcję elementu członkowskiego w klasach [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo), [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)i [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo).

Obiekty pól nie są reprezentowane przez klasę MFC. Zamiast tego obiekty DAO leżące u podstaw obiektów MFC następujących klas zawierają kolekcje obiektów pól: [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)i [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Te klasy dostarczają funkcji członkowskich, aby uzyskać dostęp do niektórych pojedynczych `CDaoFieldInfo` elementów `GetFieldInfo` informacji o polu lub można uzyskać do nich dostęp wszystkie naraz z obiektu, wywołując funkcję elementu członkowskiego obiektu zawierającego.

Oprócz jego zastosowania do badania właściwości obiektu, `CDaoFieldInfo` można również użyć do konstruowania parametru wejściowego do tworzenia nowych pól w tabledef. Prostsze opcje są dostępne dla tego zadania, ale jeśli chcesz lepszą kontrolę, można użyć wersji [CDaoTableDef::CreateField,](../../mfc/reference/cdaotabledef-class.md#createfield) który przyjmuje `CDaoFieldInfo` parametr.

Informacje pobierane `GetFieldInfo` przez funkcję elementu członkowskiego (klasy zawierającej pole) są przechowywane w `CDaoFieldInfo` strukturze. Wywołanie `GetFieldInfo` funkcji elementu członkowskiego obiektu zawierającego, w którego fields kolekcji obiekt pola jest przechowywany. `CDaoFieldInfo`definiuje również `Dump` funkcję elementu członkowskiego w kompilacjach debugowania. Można użyć `Dump` do zrzutu `CDaoFieldInfo` zawartości obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)<br/>
[CDaoRecordset::GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)<br/>
[CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)
