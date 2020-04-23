---
title: Klasa CDaoException
ms.date: 09/17/2019
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
ms.openlocfilehash: 935d7870d68554d702e2ad762e83343cb518b2b8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754727"
---
# <a name="cdaoexception-class"></a>Klasa CDaoException

Reprezentuje warunek wyjątku wynikający z klas bazy danych MFC na podstawie obiektów dostępu do danych (DAO). DAO 3.6 jest ostateczną wersją i jest uważana za przestarzałą.

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
|[CDaoException::GetErrorCount](#geterrorcount)|Zwraca liczbę błędów w kolekcji Błędy aparatu bazy danych.|
|[CDaoException::GetErrorInfo](#geterrorinfo)|Zwraca informacje o błędzie o określonym obiekcie błędu w kolekcji Błędy.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|Zawiera rozszerzony kod błędu dla każdego błędu w klasach DAO MFC.|
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|Wskaźnik do obiektu [CDaoErrorInfo zawierający](../../mfc/reference/cdaoerrorinfo-structure.md) informacje o jednym obiekcie błędu DAO.|
|[CDaoException::m_scode](#m_scode)|Wartość [SCODE](#m_scode) skojarzona z błędem.|

## <a name="remarks"></a>Uwagi

Klasa zawiera elementy członkowskie danych publicznych, których można użyć do określenia przyczyny wyjątku. `CDaoException`obiekty są konstruowane i generowane przez funkcje członkowskie klas bazy danych DAO.

> [!NOTE]
> Klasy bazy danych DAO różnią się od klas bazy danych MFC na podstawie łączności otwartej bazy danych (ODBC). Wszystkie nazwy klas bazy danych DAO mają prefiks "CDao". Nadal można uzyskać dostęp do źródeł danych ODBC z klasami DAO. Ogólnie rzecz biorąc klasy MFC oparte na DAO są bardziej zdolne niż klasy MFC oparte na ODBC; klasy oparte na DAO mogą uzyskiwać dostęp do danych, w tym za pośrednictwem sterowników ODBC, za pośrednictwem własnego aparatu bazy danych. Klasy oparte na DAO obsługują również operacje języka DDL (Data Definition Language), takie jak dodawanie tabel za pośrednictwem klas, bez konieczności bezpośredniego wywoływania DAO. Aby uzyskać informacje na temat wyjątków zgłaszanych przez klasy ODBC, zobacz [CDBException](../../mfc/reference/cdbexception-class.md).

Można uzyskać dostęp do obiektów wyjątku w zakresie wyrażenia [CATCH.](../../mfc/reference/exception-processing.md#catch) Można również `CDaoException` rzutować obiekty z własnego kodu za pomocą [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception) funkcji globalnej.

W MFC wszystkie błędy DAO są wyrażone jako `CDaoException`wyjątki typu . Po złapaniu wyjątek tego typu, można użyć `CDaoException` funkcji członkowskich do pobierania informacji z wszelkich obiektów błędów DAO przechowywanych w kolekcji errors aparatu bazy danych. W przypadku każdego błędu jeden lub więcej obiektów błędów są umieszczane w Errors kolekcji. (Zwykle kolekcja zawiera tylko jeden obiekt błędu; jeśli używasz źródła danych ODBC, jest bardziej prawdopodobne, aby uzyskać wiele obiektów błędów.) Gdy inna operacja DAO generuje błąd, errors kolekcji jest czyszczona, a nowy obiekt błędu jest umieszczany w Errors kolekcji. Operacje DAO, które nie generują błędu nie mają wpływu na błędy kolekcji.

Kody błędów DAO można znaleźć w pliku DAOERR. H. Aby uzyskać powiązane informacje, zobacz temat "Błędy dostępu do danych do zalewkowalnych" w Pomocy DAO.

Aby uzyskać więcej informacji na temat `CDaoException` obsługi wyjątków w ogóle lub o obiektach, zobacz artykuły [Obsługa wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md) i [Wyjątki: Wyjątki bazy danych](../../mfc/exceptions-database-exceptions.md). Drugi artykuł zawiera przykładowy kod, który ilustruje obsługę wyjątków w DAO.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cexception](../../mfc/reference/cexception-class.md)

`CDaoException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="cdaoexceptioncdaoexception"></a><a name="cdaoexception"></a>CDaoException::CDaoException

Konstruuje `CDaoException` obiekt.

```
CDaoException();
```

### <a name="remarks"></a>Uwagi

Zwykle struktura tworzy obiekty wyjątków, gdy jego kod zgłasza wyjątek. Rzadko trzeba utworzyć obiekt wyjątku jawnie. Jeśli chcesz rzucić `CDaoException` z własnego kodu, wywołać funkcję globalną [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception).

Jednak można jawnie utworzyć obiekt wyjątku, jeśli dokonujesz bezpośrednich wywołań DAO za pośrednictwem wskaźników interfejsu DAO, które hermetyzują klasy MFC. W takim przypadku może być konieczne pobranie informacji o błędzie z DAO. Załóżmy, że błąd występuje w DAO podczas wywoływania metody DAO za pośrednictwem interfejsu DAODatabases do kolekcji baz danych obszaru roboczego.

##### <a name="to-retrieve-the-dao-error-information"></a>Aby pobrać informacje o błędzie DAO

1. Konstruuj `CDaoException` obiekt.

1. Wywołanie funkcji elementu członkowskiego [GetErrorCount](#geterrorcount) obiektu wyjątku, aby określić, ile obiektów błędów znajduje się w kolekcji Errors aparatu bazy danych. (Zwykle tylko jeden, chyba że używasz źródła danych ODBC.)

1. Wywołanie funkcji elementu członkowskiego [GetErrorInfo](#geterrorinfo) obiektu wyjątku, aby pobrać jeden określony obiekt błędu w czasie, przez indeks w kolekcji, za pośrednictwem obiektu wyjątku. Pomyśl o obiekcie wyjątku jako proxy dla jednego obiektu błędu DAO.

1. Sprawdź bieżącą strukturę [CDaoErrorInfo,](../../mfc/reference/cdaoerrorinfo-structure.md) która `GetErrorInfo` zwraca w [m_pErrorInfo](#m_perrorinfo) element członkowski danych. Jego członkowie dostarczają informacji na temat błędu DAO.

1. W przypadku źródła danych ODBC powtórz kroki 3 i 4 w razie potrzeby, aby uzyskać więcej obiektów błędów.

1. Jeśli obiekt wyjątku został skonstruowany na stercie, usuń go za pomocą operatora **delete** po zakończeniu.

Aby uzyskać więcej informacji na temat obsługi błędów w klasach DAO MFC, zobacz artykuł [Wyjątki: Wyjątki bazy danych](../../mfc/exceptions-database-exceptions.md).

## <a name="cdaoexceptiongeterrorcount"></a><a name="geterrorcount"></a>CDaoException::GetErrorCount

Wywołanie tej funkcji elementu członkowskiego, aby pobrać liczbę obiektów błędów DAO w kolekcji errors aparatu bazy danych.

```
short GetErrorCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba obiektów błędów DAO w kolekcji Błędy aparatu bazy danych.

### <a name="remarks"></a>Uwagi

Te informacje są przydatne do pętli za pośrednictwem errors kolekcji, aby pobrać każdy z jednego lub więcej obiektów błędu DAO w kolekcji. Aby pobrać obiekt błędu według indeksu lub numeru błędu DAO, należy wywołać funkcję elementu członkowskiego [GetErrorInfo.](#geterrorinfo)

> [!NOTE]
> Zwykle istnieje tylko jeden obiekt błędu w Errors kolekcji. Jeśli pracujesz ze źródłem danych ODBC, jednak może być więcej niż jeden.

## <a name="cdaoexceptiongeterrorinfo"></a><a name="geterrorinfo"></a>CDaoException::GetErrorInfo

Zwraca informacje o błędzie o określonym obiekcie błędu w kolekcji Błędy.

```cpp
void GetErrorInfo(int nIndex);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks informacji o błędzie w kolekcji Błędy aparatu bazy danych, do wyszukiwania według indeksu.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać następujące rodzaje informacji o wyjątku:

- Kod błędu

- Element źródłowy

- Opis

- Plik Pomocy

- Kontekst Pomocy

`GetErrorInfo`przechowuje informacje w elementów `m_pErrorInfo` członkowskich danych obiektu wyjątku. Aby uzyskać krótki opis zwróconych informacji, zobacz [m_pErrorInfo](#m_perrorinfo). Jeśli złapiesz wyjątek typu `CDaoException` zgłaszanego `m_pErrorInfo` przez MFC, element członkowski zostanie już wypełniony. Jeśli zdecydujesz się wywołać DAO bezpośrednio, należy wywołać funkcję `GetErrorInfo` elementu `m_pErrorInfo`członkowskiego obiektu wyjątku samodzielnie, aby wypełnić . Aby uzyskać bardziej szczegółowy opis, zobacz [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) struktury.

Aby uzyskać informacje na temat wyjątków DAO i przykładowego kodu, zobacz artykuł [Wyjątki: Wyjątki bazy danych](../../mfc/exceptions-database-exceptions.md).

## <a name="cdaoexceptionm_nafxdaoerror"></a><a name="m_nafxdaoerror"></a>CDaoException::m_nAfxDaoError

Zawiera rozszerzony kod błędu MFC.

### <a name="remarks"></a>Uwagi

Ten kod jest dostarczany w przypadkach, gdy określony składnik klas DAO MFC popełnił błąd.

Możliwe wartości:

- NO_AFX_DAO_ERROR Najnowsza operacja nie spowodowało rozszerzonego błędu MFC. Jednak operacja mogła spowodować inne błędy z DAO lub OLE, więc należy [sprawdzić, m_pErrorInfo](#m_perrorinfo) i ewentualnie [m_scode](#m_scode).

- AFX_DAO_ERROR_ENGINE_INITIALIZATION MFC nie może zainicjować aparatu bazy danych Microsoft Jet. Ole może nie można zainicjować lub może być niemożliwe do utworzenia wystąpienia obiektu aparatu bazy danych DAO. Te problemy zwykle sugerują złą instalację dao lub OLE.

- AFX_DAO_ERROR_DFX_BIND Adres używany w wywołaniu funkcji wymiany pól rekordu DAO (DFX) nie istnieje lub jest nieprawidłowy (adres nie był używany do powiązania danych). Być może przeszedłeś zły adres w wywołaniu DFX lub adres mógł stać się nieprawidłowy między operacjami DFX.

- AFX_DAO_ERROR_OBJECT_NOT_OPEN Próbowano otworzyć a recordset na podstawie querydef lub tabledef obiektu, który nie był w stanie otwartym.

## <a name="cdaoexceptionm_perrorinfo"></a><a name="m_perrorinfo"></a>CDaoException::m_pErrorInfo

Zawiera wskaźnik do `CDaoErrorInfo` struktury, który zawiera informacje o obiekcie błędu DAO, który został ostatnio pobrany przez wywołanie [GetErrorInfo](#geterrorinfo).

### <a name="remarks"></a>Uwagi

Ten obiekt zawiera następujące informacje:

|Członek CDaoErrorInfo|Informacje|Znaczenie|
|--------------------------|-----------------|-------------|
|`m_lErrorCode`|Kod błędu|Kod błędu DAO|
|`m_strSource`|Element źródłowy|Nazwa obiektu lub aplikacji, która pierwotnie wygenerowała błąd|
|`m_strDescription`|Opis|Ciąg opisowy skojarzony z błędem|
|`m_strHelpFile`|Plik Pomocy|Ścieżka do pliku Pomocy systemu Windows, w którym użytkownik może uzyskać informacje o problemie|
|`m_lHelpContext`|Kontekst pomocy|Identyfikator kontekstu tematu w pliku Pomocy DAO|

Aby uzyskać szczegółowe informacje na `CDaoErrorInfo` temat informacji zawartych w obiekcie, zobacz [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) struktury.

## <a name="cdaoexceptionm_scode"></a><a name="m_scode"></a>CDaoException::m_scode

Zawiera wartość typu `SCODE` opisującą błąd.

### <a name="remarks"></a>Uwagi

Jest to kod OLE. Rzadko trzeba będzie używać tej wartości, ponieważ w prawie wszystkich przypadkach bardziej szczegółowe informacje o `CDaoException` błędach MFC lub DAO są dostępne w innych elementów członkowskich danych.

Aby uzyskać informacje na temat SCODE, zobacz temat [Struktura kodów błędów OLE](/windows/win32/com/structure-of-com-error-codes) w windows SDK. Typ danych SCODE jest mapowany na typ danych HRESULT.

## <a name="see-also"></a>Zobacz też

[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CException](../../mfc/reference/cexception-class.md)
