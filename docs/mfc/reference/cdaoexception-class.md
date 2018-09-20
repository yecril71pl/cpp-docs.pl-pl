---
title: Klasa CDaoException | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoException
- AFXDAO/CDaoException
- AFXDAO/CDaoException::CDaoException
- AFXDAO/CDaoException::GetErrorCount
- AFXDAO/CDaoException::GetErrorInfo
- AFXDAO/CDaoException::m_nAfxDaoError
- AFXDAO/CDaoException::m_pErrorInfo
- AFXDAO/CDaoException::m_scode
dev_langs:
- C++
helpviewer_keywords:
- CDaoException [MFC], CDaoException
- CDaoException [MFC], GetErrorCount
- CDaoException [MFC], GetErrorInfo
- CDaoException [MFC], m_nAfxDaoError
- CDaoException [MFC], m_pErrorInfo
- CDaoException [MFC], m_scode
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 38ac86784216fdc81eb73c56f82e8f7b6744941d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431817"
---
# <a name="cdaoexception-class"></a>Klasa CDaoException

Przedstawia warunek wyjątku wynikający z klas baz danych MFC na podstawie obiektów dostępu do danych (DAO).

## <a name="syntax"></a>Składnia

```
class CDaoException : public CException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoException::CDaoException](#cdaoexception)|Konstruuje `CDaoException` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoException::GetErrorCount](#geterrorcount)|Zwraca liczbę wszystkich błędów w kolekcji błędów aparatu bazy danych.|
|[CDaoException::GetErrorInfo](#geterrorinfo)|Zwraca informacje o błędzie o obiekcie określony błąd w kolekcji błędów.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|Zawiera kod błędu rozszerzonego wszelkie błędy do klas MFC DAO.|
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|Wskaźnik do [cdaoerrorinfo —](../../mfc/reference/cdaoerrorinfo-structure.md) obiektu, który zawiera informacje dotyczące jednego obiektu błąd DAO.|
|[CDaoException::m_scode](#m_scode)|[SCODE](#m_scode) wartość skojarzoną z powodu błędu.|

## <a name="remarks"></a>Uwagi

Klasa zawiera publiczne elementy członkowskie danych używane w celu ustalenia przyczyny wyjątku. `CDaoException` obiekty są zbudowane i generowane przez funkcje składowe klas baz danych DAO.

> [!NOTE]
>  Klasy bazy danych DAO różnią się od klas baz danych MFC, które są oparte na Open Database Connectivity (ODBC). Wszystkie nazwy klasy bazy danych DAO mają prefiks "CDao". Możesz nadal dostęp do źródła danych ODBC przy użyciu klas DAO. Ogólnie rzecz biorąc klasy MFC, w oparciu o DAO sprzętowi więcej niż klas MFC, w oparciu o ODBC; klasy oparte na DAO można uzyskać dostęp do danych, w tym za pomocą sterowników ODBC, za pomocą ich własnych aparatu bazy danych. Klasy oparte na DAO obsługują także operacji języka definicji danych (DDL), takich jak dodawanie tablic przy użyciu klas, bez konieczności wywoływanie obiektów DAO bezpośrednio. Aby uzyskać informacji na temat wyjątków zgłaszanych przez klasy ODBC, zobacz [CDBException](../../mfc/reference/cdbexception-class.md).

Możesz uzyskać dostęp obiektów wyjątków w zakresie [CATCH](../../mfc/reference/exception-processing.md#catch) wyrażenia. Może również zgłosić `CDaoException` obiektów w kodzie za pomocą [afxthrowdaoexception —](../../mfc/reference/exception-processing.md#afxthrowdaoexception) funkcja globalna.

W MFC, wszystkie błędy DAO są wyrażane jako wyjątków typu `CDaoException`. Jeśli przechwytujesz wyjątek tego typu, możesz użyć `CDaoException` funkcji elementów członkowskich, aby pobrać informacje z wszystkie obiekty błąd DAO, przechowywane w kolekcji błędów aparatu bazy danych. Ponieważ każdy błąd wystąpi, co najmniej jeden obiekt błędu są umieszczane w kolekcji błędów. (Zazwyczaj kolekcja zawiera tylko jeden obiekt błąd; Jeśli używasz źródła danych ODBC, jest bardziej prawdopodobne, można pobrać wiele obiektów błędu). Gdy inna operacja DAO generuje błąd, zbierania błędów jest wyczyszczone, a nowy obiekt błędu jest umieszczany w kolekcji błędów. Operacje DAO, które nie generuje błąd nie mają wpływu na kolekcji błędów.

Aby uzyskać kody błędów DAO zobacz plik DAOERR. H. Aby uzyskać powiązane informacje zobacz temat "Możliwe do wychwycenia błędami dostępu do danych" w Pomocy programu DAO.

Aby uzyskać więcej informacji na temat obsługi wyjątków w ogólne lub wkrótce `CDaoException` obiektów, zobacz artykuły [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md) i [wyjątki: wyjątki bazy danych](../../mfc/exceptions-database-exceptions.md). Drugi artykuł zawiera przykładowy kod, który ilustruje wyjątków w DAO.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDaoException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

##  <a name="cdaoexception"></a>  CDaoException::CDaoException

Konstruuje `CDaoException` obiektu.

```
CDaoException();
```

### <a name="remarks"></a>Uwagi

Zazwyczaj szablon tworzy obiekty wyjątków, po jego kod zgłasza wyjątek. Rzadko, musisz jawnie utworzyć obiekt wyjątku. Jeśli chcesz wygenerować `CDaoException` z własnego kodu, wywołanie funkcji globalnych [afxthrowdaoexception —](../../mfc/reference/exception-processing.md#afxthrowdaoexception).

Jednakże można jawnie utworzyć obiekt wyjątku, jeśli wykonujesz bezpośrednich wywołań do DAO za pośrednictwem DAO wskaźniki interfejsu, które hermetyzują klas MFC. W takim przypadku konieczne może pobrać informacji o błędzie z DAO. Załóżmy, że po wywołaniu metody DAO za pośrednictwem interfejsu DAODatabases kolekcji baz danych obszaru roboczego w DAO wystąpi błąd.

##### <a name="to-retrieve-the-dao-error-information"></a>Aby pobrać informacje o błędzie DAO

1. Konstruowania `CDaoException` obiektu.

1. Wywołanie obiektu wyjątku [GetErrorCount](#geterrorcount) funkcja elementu członkowskiego, aby ustalić, ile obiektów błędu znajdują się w kolekcji błędów aparatu bazy danych. (Zwykle tylko jeden, chyba że używasz źródła danych ODBC.)

1. Wywołanie obiektu wyjątku [geterrorinfo —](#geterrorinfo) funkcję elementu członkowskiego, aby pobrać jeden obiekt konkretny błąd w czasie, przez indeks w kolekcji, za pomocą obiektu wyjątku. Obiekt wyjątku można traktować jako serwer proxy dla jednego obiektu błąd DAO.

1. Sprawdź bieżące [cdaoerrorinfo —](../../mfc/reference/cdaoerrorinfo-structure.md) struktury, która `GetErrorInfo` zwraca [m_pErrorInfo](#m_perrorinfo) element członkowski danych. Jej członków zawierają informacje o błędzie DAO.

1. W przypadku źródła danych ODBC Powtórz kroki 3 i 4, zgodnie z potrzebami, więcej obiektów błędu.

1. Jeśli tworzony jest obiekt wyjątku na stosie, usuń ją za pomocą **Usuń** operator podczas kończenia pracy.

Aby uzyskać więcej informacji na temat obsługi błędów w klas MFC DAO, zobacz artykuł [wyjątki: wyjątki bazy danych](../../mfc/exceptions-database-exceptions.md).

##  <a name="geterrorcount"></a>  CDaoException::GetErrorCount

Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę obiektów błąd DAO w kolekcji błędów aparatu bazy danych.

```
short GetErrorCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba obiektów błąd DAO w kolekcji błędów aparatu bazy danych.

### <a name="remarks"></a>Uwagi

Te informacje są przydatne do kolekcji błędów, które można pobrać każdy z co najmniej jeden błąd obiektów DAO w kolekcji w pętli. Aby pobrać obiekt błędu, za pomocą indeksu lub numer błędu DAO, należy wywołać [geterrorinfo —](#geterrorinfo) funkcja elementu członkowskiego.

> [!NOTE]
>  Zazwyczaj jest tylko jeden błąd obiekt w kolekcji błędów. Jeśli pracujesz z źródła danych ODBC, jednak mogą występować więcej niż jeden.

##  <a name="geterrorinfo"></a>  CDaoException::GetErrorInfo

Zwraca informacje o błędzie o obiekcie określony błąd w kolekcji błędów.

```
void GetErrorInfo(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks informacji o błędzie w kolekcji błędów aparatu bazy danych, do wyszukiwania według indeksu.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać następujące rodzaje informacji o wyjątku:

- Kod błędu:

- Źródło

- Opis

- Plik pomocy

- Pomoc kontekstowa

`GetErrorInfo` zapisuje informacje w obiekt wyjątku `m_pErrorInfo` element członkowski danych. Aby uzyskać krótki opis zwrócone informacje, zobacz [m_pErrorInfo](#m_perrorinfo). Jeśli przechwytujesz wyjątek typu `CDaoException` zgłoszony przez MFC, `m_pErrorInfo` elementu członkowskiego już być wypełnione. Jeśli zdecydujesz się wywoływanie obiektów DAO bezpośrednio, należy wywołać obiekt wyjątku `GetErrorInfo` funkcja elementu członkowskiego sobie, aby wypełnić `m_pErrorInfo`. Aby uzyskać bardziej szczegółowy opis, zobacz [cdaoerrorinfo —](../../mfc/reference/cdaoerrorinfo-structure.md) struktury.

Aby uzyskać informacji dotyczących wyjątków DAO i przykładowy kod, zobacz artykuł [wyjątki: wyjątki bazy danych](../../mfc/exceptions-database-exceptions.md).

##  <a name="m_nafxdaoerror"></a>  CDaoException::m_nAfxDaoError

Zawiera MFC, rozszerzony kod błędu.

### <a name="remarks"></a>Uwagi

Ten kod jest dostarczany w przypadkach, w którym ma erred określonego składnika klas MFC DAO.

Możliwe wartości to:

- Błąd rozszerzony NO_AFX_DAO_ERROR, który ostatnią czynność nie powoduje MFC. Jednak operacja może zostały utworzone inne błędy z DAO lub OLE, ale należy sprawdzić, [m_pErrorInfo](#m_perrorinfo) i ewentualnie [m_scode](#m_scode).

- AFX_DAO_ERROR_ENGINE_INITIALIZATION MFC nie można zainicjować aparatu bazy danych Microsoft Jet. OLE może nie można zainicjować lub było niemożliwe utworzyć wystąpienie obiektu aparatu bazy danych DAO. Te problemy zwykle sugerują zły instalacji DAO lub OLE.

- AFX_DAO_ERROR_DFX_BIND adres używany w wywołaniu funkcji wymiany (DXF) pola rekordów DAO nie istnieje lub jest nieprawidłowy (adres nie był używany do powiązania danych). Zły adres może mieć upłynęło w wywołaniu DFX lub adres mogły stać się nieprawidłowe między operacjami DFX.

- AFX_DAO_ERROR_OBJECT_NOT_OPEN próbowano otworzyć zestawu rekordów na podstawie querydef lub obiekt tabledef, który nie był w stanie otwartym.

##  <a name="m_perrorinfo"></a>  CDaoException::m_pErrorInfo

Zawiera wskaźnik do `CDaoErrorInfo` strukturę, która zawiera informacje na temat obiekt DAO błąd ostatniego pobrania przez wywołanie metody [geterrorinfo —](#geterrorinfo).

### <a name="remarks"></a>Uwagi

Ten obiekt zawiera następujące informacje:

|Cdaoerrorinfo — element członkowski|Informacje|Znaczenie|
|--------------------------|-----------------|-------------|
|`m_lErrorCode`|Kod błędu|Kod błędu DAO|
|`m_strSource`|Źródło|Nazwa obiektu lub aplikacji, który początkowo wygenerował błąd|
|`m_strDescription`|Opis|Opisowy ciąg skojarzony z błędem|
|`m_strHelpFile`|Plik pomocy|Ścieżka do pliku Pomocy Windows, w której użytkownik może uzyskać informacji o problemie|
|`m_lHelpContext`|Pomoc kontekstowa|Identyfikator kontekstu dla tematu w pliku pomocy DAO|

Aby uzyskać szczegółowe informacje o informacje zawarte w `CDaoErrorInfo` obiektu, zobacz [cdaoerrorinfo —](../../mfc/reference/cdaoerrorinfo-structure.md) struktury.

##  <a name="m_scode"></a>  CDaoException::m_scode

Zawiera wartość typu `SCODE` , który opisuje błąd.

### <a name="remarks"></a>Uwagi

Jest to kod OLE. Rzadko będą musieli używać tej wartości, ponieważ prawie we wszystkich przypadkach, bardziej szczegółowe informacje o błędach i DAO MFC jest dostępna w innych `CDaoException` składowych danych.

Aby uzyskać informacje na temat SCODE, zobacz temat [struktury z OLE kody błędów](/windows/desktop/com/structure-of-com-error-codes) w zestawie Windows SDK. Typ danych SCODE mapuje na typ HRESULT.

## <a name="see-also"></a>Zobacz też

[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CException](../../mfc/reference/cexception-class.md)
