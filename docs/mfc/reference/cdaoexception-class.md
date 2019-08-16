---
title: Klasa CDaoException
ms.date: 11/04/2016
f1_keywords:
- CDaoException
- AFXDAO/CDaoException
- AFXDAO/CDaoException::CDaoException
- AFXDAO/CDaoException::GetErrorCount
- AFXDAO/CDaoException::GetErrorInfo
- AFXDAO/CDaoException::m_nAfxDaoError
- AFXDAO/CDaoException::m_pErrorInfo
- AFXDAO/CDaoException::m_scode
helpviewer_keywords:
- CDaoException [MFC], CDaoException
- CDaoException [MFC], GetErrorCount
- CDaoException [MFC], GetErrorInfo
- CDaoException [MFC], m_nAfxDaoError
- CDaoException [MFC], m_pErrorInfo
- CDaoException [MFC], m_scode
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
ms.openlocfilehash: e5f28b8896fc9e7e5c6a656a64b938cd7af39f42
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507062"
---
# <a name="cdaoexception-class"></a>Klasa CDaoException

Reprezentuje warunek wyjątku wynikający z klas baz danych MFC opartych na obiektach dostępu do danych (DAO).

## <a name="syntax"></a>Składnia

```
class CDaoException : public CException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoException::CDaoException](#cdaoexception)|Konstruuje `CDaoException` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoException::GetErrorCount](#geterrorcount)|Zwraca liczbę błędów w kolekcji błędów aparatu bazy danych.|
|[CDaoException:: GetErrorInfo](#geterrorinfo)|Zwraca informacje o błędzie dotyczące konkretnego obiektu błędu w kolekcji błędów.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|Zawiera rozszerzony kod błędu dla dowolnego błędu w klasach MFC DAO.|
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|Wskaźnik do obiektu [CDaoErrorInfo —](../../mfc/reference/cdaoerrorinfo-structure.md) , który zawiera informacje o jednym obiekcie błędu obiektów DAO.|
|[CDaoException::m_scode](#m_scode)|Wartość [SCODE](#m_scode) skojarzona z błędem.|

## <a name="remarks"></a>Uwagi

Klasa zawiera publiczne elementy członkowskie danych, których można użyć do określenia przyczyny wyjątku. `CDaoException`obiekty są konstruowane i zgłaszane przez funkcje składowe klas baz danych DAO.

> [!NOTE]
>  Klasy bazy danych DAO różnią się od klas baz danych MFC opartych na Open Database Connectivity (ODBC). Wszystkie nazwy klas baz danych DAO mają prefiks "CDao". Nadal można uzyskać dostęp do źródeł danych ODBC przy użyciu klas DAO. Ogólnie rzecz biorąc, klasy MFC oparte na obiektach DAO są bardziej możliwością niż klasy MFC oparte na ODBC; klasy oparte na DAO mogą uzyskiwać dostęp do danych, w tym za pośrednictwem sterowników ODBC, za pośrednictwem własnego aparatu bazy danych. Klasy oparte na obiektach DAO obsługują również operacje języka definicji danych (DDL), takie jak Dodawanie tabel za pośrednictwem klas, bez konieczności bezpośredniego wywoływania obiektów DAO. Aby uzyskać informacje o wyjątkach zgłaszanych przez klasy ODBC, zobacz [CDBException](../../mfc/reference/cdbexception-class.md).

Można uzyskać dostęp do obiektów wyjątków w zakresie wyrażenia [catch](../../mfc/reference/exception-processing.md#catch) . Możesz również generować `CDaoException` obiekty z własnego kodu za pomocą funkcji globalnej [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception) .

W MFC wszystkie błędy obiektów DAO są wyrażane jako wyjątki typu `CDaoException`. Podczas przechwytywania wyjątku tego typu, można użyć `CDaoException` funkcji składowych, aby pobrać informacje z dowolnego obiektów błędów DAO przechowywanych w kolekcji błędów aparatu bazy danych. W przypadku wystąpienia każdego błędu jeden lub więcej obiektów błędów jest umieszczanych w kolekcji błędy. (Zazwyczaj kolekcja zawiera tylko jeden obiekt błędu). Jeśli używasz źródła danych ODBC, najtrudniejsze jest uzyskanie wielu obiektów błędów. Gdy inna operacja DAO generuje błąd, kolekcja błędy zostanie wyczyszczona, a nowy obiekt błędu zostanie umieszczony w kolekcji błędów. Operacje DAO, które nie generują błędu, nie mają wpływu na zbieranie błędów.

W przypadku kodów błędów DAO zobacz plik DAOERR. C. Aby uzyskać powiązane informacje, zobacz temat "błędy dostępu do danych z pułapkami" w pomocy programu DAO.

Aby uzyskać więcej informacji na temat obsługi wyjątków ogólnie lub na `CDaoException` temat obiektów, zobacz [Obsługa wyjątków artykułów (MFC)](../../mfc/exception-handling-in-mfc.md) i [wyjątki: Wyjątki](../../mfc/exceptions-database-exceptions.md)bazy danych. Drugi artykuł zawiera przykładowy kod, który ilustruje obsługę wyjątków w DAO.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDaoException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

##  <a name="cdaoexception"></a>CDaoException::CDaoException

Konstruuje `CDaoException` obiekt.

```
CDaoException();
```

### <a name="remarks"></a>Uwagi

Zwykle struktura tworzy obiekty wyjątków, gdy jego kod zgłasza wyjątek. Rzadko trzeba utworzyć obiekt wyjątku jawnie. Jeśli chcesz zgłosić `CDaoException` z własnego kodu, wywołaj funkcję globalną [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception).

Można jednak jawnie utworzyć obiekt wyjątku, jeśli wykonujesz bezpośrednie wywołania DAO za pośrednictwem wskaźników interfejsu DAO, które są hermetyzowane przez klasy MFC. W takim przypadku może być konieczne pobranie informacji o błędzie z obiektów DAO. Załóżmy, że w programie DAO występuje błąd, gdy wywoływana jest metoda DAO za pośrednictwem interfejsu DAODatabases do kolekcji baz danych obszaru roboczego.

##### <a name="to-retrieve-the-dao-error-information"></a>Aby pobrać informacje o błędzie DAO

1. Konstruowanie `CDaoException` obiektu.

1. Wywołaj funkcję elementu członkowskiego [GetErrorCount](#geterrorcount) obiektu wyjątku, aby określić, ile obiektów błędów znajduje się w kolekcji błędów aparatu bazy danych. (Zwykle tylko jeden, chyba że używasz źródła danych ODBC).

1. Wywołaj funkcję członkowską [GetErrorInfo](#geterrorinfo) obiektu Exception, aby pobrać jeden konkretny obiekt błędu w danym momencie przez indeks w kolekcji, za pośrednictwem obiektu Exception. Obiekt wyjątku należy traktować jako serwer proxy dla jednego obiektu błędu DAO.

1. Przeanalizuj bieżącą strukturę [CDaoErrorInfo —](../../mfc/reference/cdaoerrorinfo-structure.md) , `GetErrorInfo` która zwraca wartość w elemencie członkowskim danych [m_pErrorInfo](#m_perrorinfo) . Jego członkowie dostarczają informacji o błędzie DAO.

1. W przypadku źródła danych ODBC Powtórz kroki 3 i 4 w razie potrzeby, aby uzyskać więcej obiektów błędów.

1. Jeśli obiekt Exception został skonstruowany na stercie, usuń go z operatorem **delete** po zakończeniu.

Aby uzyskać więcej informacji na temat obsługi błędów w klasach MFC DAO, zobacz [wyjątki artykułów: Wyjątki](../../mfc/exceptions-database-exceptions.md)bazy danych.

##  <a name="geterrorcount"></a>CDaoException::GetErrorCount

Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę obiektów błędów DAO w kolekcji błędów aparatu bazy danych.

```
short GetErrorCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba obiektów błędów DAO w kolekcji błędów aparatu bazy danych.

### <a name="remarks"></a>Uwagi

Te informacje są przydatne w przypadku zapętlenia w kolekcji błędy w celu pobrania każdego z jednego lub większej liczby obiektów błędów DAO w kolekcji. Aby pobrać obiekt błędu według indeksu lub liczby błędów DAO, wywołaj funkcję członkowską [GetErrorInfo](#geterrorinfo) .

> [!NOTE]
>  Zwykle w kolekcji błędów występuje tylko jeden obiekt Error. Jeśli pracujesz ze źródłem danych ODBC, jednak może istnieć więcej niż jeden.

##  <a name="geterrorinfo"></a>CDaoException:: GetErrorInfo

Zwraca informacje o błędzie dotyczące konkretnego obiektu błędu w kolekcji błędów.

```
void GetErrorInfo(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks informacji o błędzie w kolekcji błędów aparatu bazy danych dla wyszukiwania według indeksu.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać następujące rodzaje informacji o wyjątku:

- Kod błędu

- Source

- Opis

- Plik pomocy

- Kontekst pomocy

`GetErrorInfo`przechowuje informacje w elemencie członkowskim `m_pErrorInfo` danych obiektu Exception. Aby uzyskać krótki opis zwracanych informacji, zobacz [m_pErrorInfo](#m_perrorinfo). W przypadku przechwycenia wyjątku typu `CDaoException` zgłoszonego przez MFC `m_pErrorInfo` , element członkowski zostanie już wypełniony. W przypadku wybrania bezpośredniego wywoływania obiektów DAO należy wywoływać funkcję `GetErrorInfo` elementu członkowskiego obiektu wyjątku do wypełnienia. `m_pErrorInfo` Aby uzyskać bardziej szczegółowy opis, zobacz strukturę [CDaoErrorInfo —](../../mfc/reference/cdaoerrorinfo-structure.md) .

Aby uzyskać informacje o wyjątkach DAO i przykładowym kodzie, zobacz [wyjątki w artykule: Wyjątki](../../mfc/exceptions-database-exceptions.md)bazy danych.

##  <a name="m_nafxdaoerror"></a>CDaoException::m_nAfxDaoError

Zawiera rozszerzony kod błędu MFC.

### <a name="remarks"></a>Uwagi

Ten kod jest dostarczany w przypadkach, gdy określony składnik klas MFC DAO ma erred.

Możliwe wartości to:

- NO_AFX_DAO_ERROR ostatniej operacji nie spowodowało rozszerzonego błędu MFC. Jednak operacja mogła wydawać inne błędy z obiektów DAO lub OLE, dlatego należy sprawdzać [m_pErrorInfo](#m_perrorinfo) i [m_scode](#m_scode).

- AFX_DAO_ERROR_ENGINE_INITIALIZATION MFC nie może zainicjować aparatu bazy danych Microsoft Jet. Zainicjowanie interfejsu OLE nie powiodło się lub nie można było utworzyć wystąpienia obiektu aparatu bazy danych DAO. Te problemy zwykle sugerują nieprawidłową instalację obiektu DAO lub OLE.

- AFX_DAO_ERROR_DFX_BIND adres użyty w wywołaniu funkcji programu Exchange Field Record (DFX) obiektu DAO nie istnieje lub jest nieprawidłowy (adres nie został użyty do powiązania danych). Mógł zostać przeprowadzony niewłaściwy adres w wywołaniu DFX lub adres stał się nieprawidłowy między operacjami DFX.

- AFX_DAO_ERROR_OBJECT_NOT_OPEN próbowano otworzyć zestaw rekordów na podstawie obiektu querydef lub tabledef, który nie był w stanie otwartym.

##  <a name="m_perrorinfo"></a>CDaoException::m_pErrorInfo

Zawiera wskaźnik do `CDaoErrorInfo` struktury, która zawiera informacje dotyczące obiektu błędu DAO, który został ostatnio pobrany przez wywołanie metody [GetErrorInfo](#geterrorinfo).

### <a name="remarks"></a>Uwagi

Ten obiekt zawiera następujące informacje:

|CDaoErrorInfo — element członkowski|Informacje|Znaczenie|
|--------------------------|-----------------|-------------|
|`m_lErrorCode`|Kod błędu|Kod błędu DAO|
|`m_strSource`|Source|Nazwa obiektu lub aplikacji, która pierwotnie wygenerowała błąd|
|`m_strDescription`|Opis|Opisowy ciąg skojarzony z błędem|
|`m_strHelpFile`|Plik pomocy|Ścieżka do pliku pomocy systemu Windows, w którym użytkownik może uzyskać informacje o problemie|
|`m_lHelpContext`|Kontekst pomocy|Identyfikator kontekstu tematu w pliku pomocy DAO|

Aby uzyskać szczegółowe informacje na temat informacji zawartych w `CDaoErrorInfo` obiekcie, zobacz strukturę [CDaoErrorInfo —](../../mfc/reference/cdaoerrorinfo-structure.md) .

##  <a name="m_scode"></a>CDaoException::m_scode

Zawiera wartość typu `SCODE` opisującą błąd.

### <a name="remarks"></a>Uwagi

Jest to kod OLE. Rzadko trzeba będzie używać tej wartości, ponieważ w prawie wszystkich przypadkach są dostępne bardziej szczegółowe informacje o błędzie MFC lub DAO w innych `CDaoException` elementach członkowskich danych.

Aby uzyskać informacje na temat SCODE, zobacz [strukturę tematu kodów błędów OLE](/windows/win32/com/structure-of-com-error-codes) w Windows SDK. Typ danych SCODE jest mapowany na typ danych HRESULT.

## <a name="see-also"></a>Zobacz także

[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CException](../../mfc/reference/cexception-class.md)
