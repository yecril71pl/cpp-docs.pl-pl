---
title: Klasa CDaoFieldExchange
ms.date: 09/17/2019
f1_keywords:
- CDaoFieldExchange
- AFXDAO/CDaoFieldExchange
- AFXDAO/CDaoFieldExchange::IsValidOperation
- AFXDAO/CDaoFieldExchange::SetFieldType
- AFXDAO/CDaoFieldExchange::m_nOperation
- AFXDAO/CDaoFieldExchange::m_prs
helpviewer_keywords:
- CDaoFieldExchange [MFC], IsValidOperation
- CDaoFieldExchange [MFC], SetFieldType
- CDaoFieldExchange [MFC], m_nOperation
- CDaoFieldExchange [MFC], m_prs
ms.assetid: 350a663e-92ff-44ab-ad53-d94efa2e5823
ms.openlocfilehash: e1ce6e13b9c6045881cc0bb4114a6e11d58365c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368989"
---
# <a name="cdaofieldexchange-class"></a>Klasa CDaoFieldExchange

Obsługuje procedury wymiany pól rekordów DAO (DFX) używane przez klasy bazy danych DAO.

DAO jest obsługiwany przez pakiet Office 2013. DAO 3.6 jest ostateczną wersją i jest uważana za przestarzałą.

## <a name="syntax"></a>Składnia

```
class CDaoFieldExchange
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoFieldExchange::IsValidOperation](#isvalidoperation)|Zwraca wartość niezerowa, jeśli bieżąca operacja jest odpowiednia dla typu aktualizowanego pola.|
|[CDaoFieldExchange::SetFieldType](#setfieldtype)|Określa typ elementu członkowskiego danych zestawu rekordów — kolumny lub parametru — reprezentowanego `SetFieldType`przez wszystkie kolejne wywołania funkcji DFX do następnego wywołania .|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDaoFieldExchange::m_nOperation](#m_noperation)|Operacja DFX wykonywana przez bieżące wywołanie funkcji `DoFieldExchange` elementu członkowskiego pliku recordset.|
|[CDaoFieldExchange::m_prs](#m_prs)|Wskaźnik do pliku recordset, na którym wykonywane są operacje DFX.|

## <a name="remarks"></a>Uwagi

`CDaoFieldExchange`nie ma klasy podstawowej.

Użyj tej klasy, jeśli piszesz procedury wymiany danych dla niestandardowych typów danych; w przeciwnym razie nie będzie bezpośrednio używać tej klasy. DFX wymienia dane między członkami danych pola obiektu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) i odpowiednimi polami bieżącego rekordu w źródle danych. DFX zarządza wymianą w obu kierunkach, ze źródła danych i do źródła danych. Informacje na temat pisania niestandardowych procedur DFX można znaleźć w [informacji technicznej 53.](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)

> [!NOTE]
> Klasy bazy danych DAO różnią się od klas bazy danych MFC na podstawie łączności otwartej bazy danych (ODBC). Wszystkie nazwy klas bazy danych DAO mają prefiks "CDao". Nadal można uzyskać dostęp do źródeł danych ODBC z klasami DAO. Ogólnie rzecz biorąc klasy MFC oparte na DAO są bardziej zdolne niż klasy MFC na podstawie ODBC. Klasy oparte na DAO mogą uzyskiwać dostęp do danych, w tym za pośrednictwem sterowników ODBC, za pośrednictwem własnego aparatu bazy danych. Obsługują one również operacje języka DDL (Data Definition Language), takie jak dodawanie tabel za pośrednictwem klas zamiast wywoływania DAO samodzielnie.

> [!NOTE]
> Wymiana pól rekordów DAO (DFX) jest bardzo podobna do wymiany pól rekordu (RFX) w klasach bazy danych MFC opartych na odbc ( `CDatabase`, `CRecordset`). Jeśli rozumiesz RFX, znajdziesz go w użyciu DFX.

Obiekt `CDaoFieldExchange` udostępnia informacje kontekstowe potrzebne do wymiany pól rekordu DAO. `CDaoFieldExchange`obiekty obsługują szereg operacji, w tym parametry wiązania i elementy członkowskie danych pól oraz ustawianie różnych flag na polach bieżącego rekordu. Operacje DFX są wykonywane na członkach danych klasy recordset typów `CDaoFieldExchange`zdefiniowanych przez typ **pola** **wyliczenia** w programie . Możliwe wartości **FieldType** to:

- `CDaoFieldExchange::outputColumn`dla elementów członkowskich danych terenowych.

- `CDaoFieldExchange::param`dla elementów członkowskich danych parametrów.

Funkcja elementu członkowskiego [IsValidOperation](#isvalidoperation) jest dostępna do pisania własnych niestandardowych procedur DFX. [SetFieldType](#setfieldtype) będzie często używany w [funkcji CDaoRecordset::DoFieldExchange.](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) Aby uzyskać szczegółowe informacje na temat funkcji globalnych DFX, zobacz [Rejestrowanie funkcji wymiany pól](../../mfc/reference/record-field-exchange-functions.md). Aby uzyskać informacje na temat pisania niestandardowych procedur DFX dla własnych typów danych, zobacz [Uwaga techniczna 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CDaoFieldExchange`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="cdaofieldexchangeisvalidoperation"></a><a name="isvalidoperation"></a>CDaoFieldExchange::IsValidOperation

Jeśli piszesz własną funkcję DFX, wywołanie `IsValidOperation` na początku funkcji, aby ustalić, czy bieżąca operacja `CDaoFieldExchange::outputColumn` może `CDaoFieldExchange::param`być wykonana na określonym typie elementu członkowskiego danych pola (a lub a ).

```
BOOL IsValidOperation();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli bieżąca operacja jest odpowiednia dla typu aktualizowanego pola.

### <a name="remarks"></a>Uwagi

Niektóre operacje wykonywane przez mechanizm DFX dotyczą tylko jednego z możliwych typów pól. Postępuj zgodnie z modelem istniejących funkcji DFX.

Aby uzyskać dodatkowe informacje na temat pisania niestandardowych procedur DFX, zobacz [Uwaga techniczna 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).

## <a name="cdaofieldexchangem_noperation"></a><a name="m_noperation"></a>CDaoFieldExchange::m_nOperation

Identyfikuje operację, która ma zostać wykonana na obiekcie [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) skojarzonym z obiektem wymiany pól.

### <a name="remarks"></a>Uwagi

Obiekt `CDaoFieldExchange` dostarcza kontekst dla wielu różnych operacji DFX na tablicy rekordów.

> [!NOTE]
> Wartość PSEUDONULL opisana w operacjach MarkForAddNew i SetFieldNull poniżej jest wartością używaną do oznaczania pól Null. Mechanizm wymiany pól rekordów DAO (DFX) używa tej wartości do określenia, które pola zostały jawnie oznaczone wartością Null. PSEUDONULL nie jest wymagany dla pól [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) i [COleCurrency.](../../mfc/reference/colecurrency-class.md)

Możliwe wartości `m_nOperation` to:

|Operacja|Opis|
|---------------|-----------------|
|`AddToParameterList`|Tworzy klauzulę **PARAMETERS** instrukcji SQL.|
|`AddToSelectList`|Tworzy klauzulę **SELECT** instrukcji SQL.|
|`BindField`|Wiąże pole w bazie danych z lokalizacją pamięci w aplikacji.|
|`BindParam`|Ustawia wartości parametrów dla kwerendy zbioru rekordów.|
|`Fixup`|Ustawia stan Null dla pola.|
|`AllocCache`|Przydziela pamięć podręczną używaną do sprawdzania "brudnych" pól w zamówieniu.|
|`StoreField`|Zapisuje bieżący rekord w pamięci podręcznej.|
|`LoadField`|Przywraca buforowane zmienne członkowskie danych w zbiorze rekordów.|
|`FreeCache`|Zwalnia pamięć podręczną używaną do sprawdzania "brudnych" pól w zamówić.|
|`SetFieldNull`|Ustawia stan pola na Null i wartość PSEUDONULL.|
|`MarkForAddNew`|Oznacza pola "brudne", jeśli nie PSEUDONULL.|
|`MarkForEdit`|Oznacza pola "brudne", jeśli nie pasują do pamięci podręcznej.|
|`SetDirtyField`|Ustawia wartości pól oznaczone jako "zabrudzone".|
|`DumpField`|Zrzuca zawartość pola (tylko debug).|
|`MaxDFXOperation`|Służy do sprawdzania danych wejściowych.|

## <a name="cdaofieldexchangem_prs"></a><a name="m_prs"></a>CDaoFieldExchange::m_prs

Zawiera wskaźnik do obiektu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) skojarzonego z obiektem. `CDaoFieldExchange`

### <a name="remarks"></a>Uwagi

## <a name="cdaofieldexchangesetfieldtype"></a><a name="setfieldtype"></a>CDaoFieldExchange::SetFieldType

Zadzwoń `SetFieldType` w `CDaoRecordset` przesłonecie `DoFieldExchange` swojej klasy.

```
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Parametry

*nPusty typ pola*<br/>
Wartość **wyliczenia FieldType**, `CDaoFieldExchange`zadeklarowana w , która może być jedną z następujących wartości:

- `CDaoFieldExchange::outputColumn`

- `CDaoFieldExchange::param`

### <a name="remarks"></a>Uwagi

Zwykle ClassWizard pisze to wezwanie dla Ciebie. Jeśli piszesz własną funkcję i używasz `DoFieldExchange` kreatora do pisania funkcji, dodaj wywołania do własnej funkcji poza mapą pola. Jeśli kreator nie jest używany, nie będzie mapy pól. Wywołanie poprzedza wywołania funkcji DFX, po jednym dla każdego członka danych pola `CDaoFieldExchange::outputColumn`klasy i identyfikuje typ pola jako .

Jeśli parametryzujesz klasę zestaw rekordów, należy dodać wywołania DFX dla wszystkich elementów członkowskich danych `SetFieldType`parametrów (poza mapą pola) i poprzedzić te wywołania wywołaniem . Przekazać wartość `CDaoFieldExchange::param`. (Zamiast tego można użyć [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) i ustawić jego wartości parametrów.)

Ogólnie rzecz biorąc, każda grupa wywołań funkcji DFX skojarzonych z członkami danych `SetFieldType`pola lub członkami danych parametrów musi być poprzedzona wywołaniem . Parametr *nFieldType* każdego `SetFieldType` wywołania identyfikuje typ elementów członkowskich danych reprezentowanych przez wywołania funkcji DFX, które następują po wywołaniu. `SetFieldType`

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)
