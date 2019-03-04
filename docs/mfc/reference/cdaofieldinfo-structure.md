---
title: CDaoFieldInfo — Struktura
ms.date: 11/04/2016
f1_keywords:
- CDaoFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
ms.openlocfilehash: a5c4013a323c85ad19a3fade20f76852e053362a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275145"
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo — Struktura

`CDaoFieldInfo` Struktura zawiera informacje dotyczące obiektu pola zdefiniowane dla obiektów dostępu do danych (DAO).

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
Unikatowej nazwy obiektu pola. Aby uzyskać szczegółowe informacje zobacz temat "Nazwa właściwości" w Pomocy programu DAO.

*m_nType*<br/>
Wartość, która wskazuje typ danych pola. Aby uzyskać szczegółowe informacje zobacz temat "Właściwość Type" w Pomocy programu DAO. Wartość tej właściwości może być jedną z następujących czynności:

- `dbBoolean` Tak/nie takie same jak wartość PRAWDA/FAŁSZ

- `dbByte` Bajtów

- `dbInteger` Krótka

- `dbLong` długi

- `dbCurrency` Waluty; klasy MFC zobacz [COleCurrency](../../mfc/reference/colecurrency-class.md)

- `dbSingle` Pojedynczy

- `dbDouble` Podwójne

- `dbDate` Data/Godzina klasy MFC zobacz [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)

- `dbText` Tekst. klasy MFC zobacz [CString](../../atl-mfc-shared/reference/cstringt-class.md)

- `dbLongBinary` Długie plik binarny (OLE Object;) Możesz chcieć użyć klasy MFC [CByteArray](../../mfc/reference/cbytearray-class.md) zamiast klasy `CLongBinary` jako `CByteArray` jest bardziej rozbudowane i łatwiejsze w użyciu.

- `dbMemo` Notatka; Zobacz klasy MFC `CString`

- `dbGUID` Globalnie unikatowy identyfikator/powszechnie Unikatowy identyfikator używany przy użyciu zdalnych wywołań procedur. Aby uzyskać więcej informacji zobacz temat "Właściwość Type" w Pomocy programu DAO.

> [!NOTE]
>  Nie należy używać typów danych parametrów dla danych binarnych. To powoduje, że Twoje dane do przekazania przez warstwę tłumaczenia Unicode/ANSI, wynikiem zwiększone obciążenie i prawdopodobnie nieoczekiwany tłumaczenia.

*m_lSize*<br/>
Wartość, która określa maksymalny rozmiar w bajtach obiektu pola DAO, który zawiera tekst lub stały rozmiar obiektu pola, która zawiera wartości tekstowe lub liczbowe. Aby uzyskać szczegółowe informacje zobacz temat "Property rozmiar" w Pomocy programu DAO. Rozmiary może być jednym z następujących wartości:

|Typ|Rozmiar (bajty)|Opis|
|----------|--------------------|-----------------|
|`dbBoolean`|1 bajt|Tak/nie (tak jak PRAWDA/FAŁSZ)|
|`dbByte`|1|Byte|
|`dbInteger`|2|Liczba całkowita|
|`dbLong`|4|Długie|
|`dbCurrency`|8|Waluty ([COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|Single|
|`dbDouble`|8|Double|
|`dbDate`|8|Data/Godzina ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Tekst ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Długie plik binarny (OLE Object; [CByteArray](../../mfc/reference/cbytearray-class.md); Użyj zamiast `CLongBinary`)|
|`dbMemo`|0|Notatka ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbGUID`|16|Globalnie unikatowy identyfikator/powszechnie Unikatowy identyfikator używany przy użyciu zdalnych wywołań procedur.|

*m_lAttributes*<br/>
Określa właściwości obiektu pola zawarte tabledef, zestaw rekordów, querydef lub indeks obiektu. Wartość zwracana może być sumę tych stałych utworzone za pomocą języka C++ Alternatywy bitowej (**&#124;**) — operator:

- `dbFixedField` Rozmiaru pola jest stały (ustawienie domyślne dla pól liczbowych).

- `dbVariableField` Rozmiar pola jest zmienną (tylko w przypadku pola tekstowe).

- `dbAutoIncrField` Wartość pola dla nowych rekordów jest automatycznie zwiększany unikatowy długa liczba całkowita, nie można jej zmienić. Obsługiwane tylko w tabelach bazy danych Microsoft Jet.

- `dbUpdatableField` Można zmienić wartość pola.

- `dbDescending` Pola są sortowane malejąco (Z - A lub 0, 100) zamówienia (dotyczy tylko do pól obiektu w kolekcji pól indeks obiektu; w MFC, indeks obiektów samodzielnie znajdują się w obiektach tabledef). Pominięcie tej stałej pola są posortowane w kolejności rosnącej (A - Z lub 0 - 100) zamówienia (ustawienie domyślne).

Podczas sprawdzania, ustawienie tej właściwości, można użyć C++ bitowe — i operatora (**&**) do przetestowania określonego atrybutu. Podczas ustawiania wiele atrybutów, można je połączyć przez połączenie odpowiedniego stałe z bitowe OR (**&#124;**) — operator. Aby uzyskać szczegółowe informacje zobacz temat "Atrybuty właściwości" w Pomocy programu DAO.

*m_nOrdinalPosition*<br/>
Wartość, która określa kolejności numerycznej, w którym mają być reprezentowane przez obiekt DAO pola mają być wyświetlane względem innych pól pola. Można ustawić tę właściwość z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield). Aby uzyskać szczegółowe informacje zobacz temat "OrdinalPosition Property" w Pomocy programu DAO.

*m_bRequired*<br/>
Wskazuje, czy obiekt DAO pole wymaga wartości innej niż Null. Jeśli ta właściwość ma wartość TRUE, pole nie zezwala na wartość Null. Jeśli jest to wymagane, jest ustawiona na wartość FALSE, pole może zawierać wartości Null, a także wartości, które spełniają warunki określonej przez ustawienie właściwości AllowZeroLength i ValidationRule. Aby uzyskać szczegółowe informacje zobacz temat "Wymagana właściwość" w Pomocy programu DAO. Można ustawić tej właściwości dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_bAllowZeroLength*<br/>
Wskazuje, czy ciąg pusty ("") jest prawidłową wartością obiekt DAO pole z typem danych tekst lub. Jeśli ta właściwość ma wartość TRUE, pusty ciąg jest prawidłową wartością. Tę właściwość można ustawić na wartość FALSE, aby upewnić się, że nie można użyć pustego ciągu można ustawić wartości pola. Aby uzyskać szczegółowe informacje zobacz temat "AllowZeroLength Property" w Pomocy programu DAO. Można ustawić tej właściwości dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_lCollatingOrder*<br/>
Określa sekwencję porządek sortowania w tekście do porównywania ciągów i sortowania. Aby uzyskać szczegółowe informacje zobacz temat "Dostosowywanie Windows rejestru ustawień do Data Access" w Pomocy programu DAO. Aby uzyskać listę możliwych wartości zwracanych, zobacz `m_lCollatingOrder` członkiem [cdaodatabaseinfo —](../../mfc/reference/cdaodatabaseinfo-structure.md) struktury. Można ustawić tej właściwości dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strForeignName*<br/>
Wartość, która w relacji, określa nazwę obiektu DAO pola w obcy tabeli, która odnosi się do pola w tabeli podstawowej. Aby uzyskać szczegółowe informacje zobacz temat "ForeignName Property" w Pomocy programu DAO.

*m_strSourceField*<br/>
Wskazuje nazwę pola, które jest oryginalnego źródła danych dla pola obiektu DAO zawartych tabledef, rekordów lub obiektu querydef. Ta właściwość wskazuje się oryginalna nazwa pola, które są skojarzone z obiektem pola. Na przykład można użyć tej właściwości można określić oryginalnego źródła danych w polu zapytania, którego nazwa nie ma wpływu na nazwę pola w tabeli podstawowej. Aby uzyskać szczegółowe informacje zobacz temat "SourceField SourceTable właściwości", w Pomocy programu DAO. Można ustawić tej właściwości dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strSourceTable*<br/>
Wskazuje nazwę tabeli, która jest oryginalnego źródła danych dla pola obiektu DAO zawartych tabledef, rekordów lub obiektu querydef. Ta właściwość wskazuje skojarzone z obiektem pola oryginalnej nazwy tabeli. Na przykład można użyć tej właściwości można określić oryginalnego źródła danych w polu zapytania, którego nazwa nie ma wpływu na nazwę pola w tabeli podstawowej. Aby uzyskać szczegółowe informacje zobacz temat "SourceField SourceTable właściwości", w Pomocy programu DAO. Można ustawić tej właściwości dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strValidationRule*<br/>
Wartość, która weryfikuje dane w polu w postaci, w jakiej jest zmieniane ani dodawane do tabeli. Aby uzyskać szczegółowe informacje zobacz temat "ValidationRule Property" w Pomocy programu DAO. Można ustawić tej właściwości dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

Aby uzyskać powiązane informacje o tabledefs — zobacz `m_strValidationRule` członkiem [cdaotabledefinfo —](../../mfc/reference/cdaotabledefinfo-structure.md) struktury.

*m_strValidationText*<br/>
Wartość, która określa tekst komunikatu, który wyświetla aplikacji, jeśli wartość obiektu pola DAO nie spełnia warunków reguły walidacji, określony przez ustawienie właściwości ValidationRule. Aby uzyskać szczegółowe informacje zobacz temat "Property komunikat" w Pomocy programu DAO. Można ustawić tej właściwości dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strDefaultValue*<br/>
Wartość domyślna obiektu DAO pola. Po utworzeniu nowego rekordu ustawienia właściwości wartość domyślna jest wprowadzana automatycznie jako wartość dla pola. Aby uzyskać szczegółowe informacje zobacz temat "Właściwość DefaultValue" w Pomocy programu DAO. Można ustawić tej właściwości dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

## <a name="remarks"></a>Uwagi

Odwołania do podstawowego, pomocniczego i wszystkie powyższe wskazują, jak informacji jest zwróconych przez `GetFieldInfo` funkcja elementu członkowskiego w klasach [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo), [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo), i [ CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo).

Pole obiekty nie są reprezentowane przez klasę MFC. Zamiast tego obiekty DAO MFC obiekty następujących klas bazowych zawiera kolekcje obiektów pola: [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), i [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). W ramach tych zajęć, podaj funkcji elementów członkowskich do dostępu do niektórych poszczególne pola informacje lub uzyskiwaniu dostępu do nich w całości z `CDaoFieldInfo` obiektu przez wywołanie metody `GetFieldInfo` funkcja elementu członkowskiego krawędzi zawierającego go obiektu.

Oprócz jej na użytek sprawdzenie właściwości obiektu, można również użyć `CDaoFieldInfo` do konstruowania przy tworzeniu nowych pól w tabledef parametru wejściowego. Prostsze opcje są dostępne dla tego zadania, ale jeśli chcesz, aby uzyskać bardziej precyzyjną kontrolę, można użyć wersji [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield) przyjmującej `CDaoFieldInfo` parametru.

Informacje o pobrane przez `GetFieldInfo` funkcji składowej (typu klasy, która zawiera pole) są przechowywane w `CDaoFieldInfo` struktury. Wywołaj `GetFieldInfo` funkcja elementu członkowskiego krawędzi zawierającego go obiektu w kolekcji pól, której jest przechowywany obiekt pola. `CDaoFieldInfo` definiuje również `Dump` kompilacje funkcja elementu członkowskiego podczas debugowania. Możesz użyć `Dump` do porzucenia zawartość `CDaoFieldInfo` obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="see-also"></a>Zobacz także

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)<br/>
[CDaoRecordset::GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)<br/>
[CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)
