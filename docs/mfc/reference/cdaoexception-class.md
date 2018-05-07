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
ms.openlocfilehash: 4531d63ff7047881f20368cbeaf8e5de4136bb9f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdaoexception-class"></a>Klasa CDaoException
Reprezentuje warunku wyjątku wynikających z klasami baz danych MFC oparte na obiekty dostępu do danych (DAO).  
  
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
|[CDaoException::GetErrorCount](#geterrorcount)|Zwraca liczbę błędów w kolekcji błędów aparatu bazy danych.|  
|[CDaoException::GetErrorInfo](#geterrorinfo)|Zwraca informacje o błędzie dotyczących obiektu określony błąd w kolekcji błędów.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|Zawiera kod błędu do klas MFC DAO błąd rozszerzony.|  
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|Wskaźnik do [cdaoerrorinfo —](../../mfc/reference/cdaoerrorinfo-structure.md) obiektu, który zawiera informacje o jeden obiekt błąd DAO.|  
|[CDaoException::m_scode](#m_scode)|[SCODE](#m_scode) wartość skojarzoną z powodu błędu.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa zawiera publicznych elementów członkowskich danych używanych w celu ustalenia przyczyny wyjątku. `CDaoException` obiekty są zbudowane i zgłaszanych przez funkcje Członkowskie klas baz danych DAO.  
  
> [!NOTE]
>  Klasy baz danych DAO różnią się od klasy baz danych MFC oparte na otwarte połączenie bazy danych (ODBC). Wszystkie nazwy klasy bazy danych DAO mają prefiks "CDao". Możesz nadal dostęp do źródła danych ODBC z klasy DAO. Ogólnie rzecz biorąc klas MFC DAO w oparciu mogą więcej niż klas MFC ODBC; w oparciu klasy oparte na DAO można uzyskać dostępu do danych, w tym za pomocą sterowników ODBC, za pomocą ich własnych aparatu bazy danych. Klasy oparte na DAO również obsługiwać operacji języka definicji danych (DDL), takich jak dodawanie tabel za pomocą klasy, bez konieczności wywoływanie obiektów DAO bezpośrednio. Aby uzyskać informacje na wyjątków zgłaszanych przez klasy ODBC, zobacz [CDBException](../../mfc/reference/cdbexception-class.md).  
  
 Dostępne obiekty wyjątków w zakresie [CATCH](../../mfc/reference/exception-processing.md#catch) wyrażenia. Można również zgłosić `CDaoException` obiektów z kodu za pomocą [afxthrowdaoexception —](../../mfc/reference/exception-processing.md#afxthrowdaoexception) funkcji globalnej.  
  
 W MFC, wszystkie błędy DAO są wyrażane jako wyjątki typu `CDaoException`. Jeśli catch wyjątku tego typu, możesz użyć `CDaoException` funkcji elementów członkowskich, aby pobrać informacje z żadnych obiektów błąd DAO przechowywanych w kolekcji błędów aparatu bazy danych. Ponieważ każdy błąd wystąpi, co najmniej jeden obiekt błąd są umieszczane w kolekcji błędów. (Zazwyczaj kolekcja zawiera tylko jeden obiekt błąd; Jeśli używasz źródła danych ODBC, to bardziej prawdopodobne uzyskanie wielu obiektów błąd). Gdy inna operacja DAO generuje błąd, kolekcji błędów jest wyczyszczone, a nowy obiekt błąd znajduje się w kolekcji błędów. Operacje DAO, które nie generuje błąd nie mają wpływu na kolekcji błędów.  
  
 Kody błędów DAO można znaleźć w pliku DAOERR. H. Aby uzyskać odpowiednie informacje zobacz temat "Przechwytywalny błędami dostępu do danych" w pomocy DAO.  
  
 Aby uzyskać więcej informacji na temat obsługi wyjątków w ogólne lub o `CDaoException` obiektów, zobacz artykuły [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md) i [wyjątki: wyjątki bazy danych](../../mfc/exceptions-database-exceptions.md). Drugi artykuł zawiera przykładowy kod, który ilustruje, obsługa wyjątków w DAO.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cexception —](../../mfc/reference/cexception-class.md)  
  
 `CDaoException`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
##  <a name="cdaoexception"></a>  CDaoException::CDaoException  
 Konstruuje `CDaoException` obiektu.  
  
```  
CDaoException();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwykle platformę tworzy obiekty wyjątków podczas jego kod zgłasza wyjątek. Rzadko występuje konieczność utworzenia jawnie obiektu wyjątku. Jeśli chcesz zgłosić `CDaoException` z własnego kodu wywołanie funkcji globalnych [afxthrowdaoexception —](../../mfc/reference/exception-processing.md#afxthrowdaoexception).  
  
 Można jawnie utworzyć obiektu wyjątków w przypadku wprowadzania bezpośrednie wywołania do DAO za pośrednictwem DAO wskaźniki interfejsu, które hermetyzują klas MFC. W takim przypadku konieczne może pobrać informacji o błędzie z DAO. Załóżmy, że podczas wywołania metody DAO za pośrednictwem interfejsu DAODatabases do kolekcji baz danych obszaru roboczego w DAO występuje błąd.  
  
##### <a name="to-retrieve-the-dao-error-information"></a>Aby pobrać informacje o błędzie DAO  
  
1.  Utworzyć `CDaoException` obiektu.  
  
2.  Wywołać obiekt wyjątku [GetErrorCount](#geterrorcount) funkcji członkowskiej, aby określić, ile obiekty błędu znajdują się w kolekcji błędów aparatu bazy danych. (Zazwyczaj tylko jeden, jeśli nie używasz źródła danych ODBC.)  
  
3.  Wywołać obiekt wyjątku [GetErrorInfo](#geterrorinfo) funkcji członkowskiej pobrać jeden obiekt błędu w czasie, przez indeks w kolekcji, za pośrednictwem obiekt wyjątku. Obiekt wyjątku można traktować jako serwer proxy dla jednego obiektu błąd DAO.  
  
4.  Sprawdź bieżący [cdaoerrorinfo —](../../mfc/reference/cdaoerrorinfo-structure.md) struktury, która `GetErrorInfo` zwraca [m_pErrorInfo](#m_perrorinfo) element członkowski danych. Jej elementów członkowskich zawierają informacje na temat błędu DAO.  
  
5.  W przypadku źródła danych ODBC Powtórz kroki 3 i 4 w razie potrzeby więcej obiektów błędu.  
  
6.  Jeśli tworzony jest obiekt wyjątku na stosie, usuń go z **usunąć** operator po zakończeniu.  
  
 Aby uzyskać więcej informacji na temat obsługi błędów w klas MFC DAO, zobacz artykuł [wyjątki: wyjątki bazy danych](../../mfc/exceptions-database-exceptions.md).  
  
##  <a name="geterrorcount"></a>  CDaoException::GetErrorCount  
 Wywołanie tej funkcji Członkowskich, aby pobrać liczbę obiektów DAO błąd w kolekcji błędów aparatu bazy danych.  
  
```  
short GetErrorCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba obiektów DAO błąd w kolekcji błędów aparatu bazy danych.  
  
### <a name="remarks"></a>Uwagi  
 Informacje te są przydatne do kolekcji błędów można pobrać każdego z co najmniej jeden błąd obiektów DAO w kolekcji w pętli. Aby pobrać obiekt błędu przez indeks lub DAO numer błędu, należy wywołać [GetErrorInfo](#geterrorinfo) funkcję elementu członkowskiego.  
  
> [!NOTE]
>  Zwykle istnieje tylko jeden obiekt błąd w kolekcji błędów. Jeśli pracujesz z źródła danych ODBC, jednak może istnieć więcej niż jeden.  
  
##  <a name="geterrorinfo"></a>  CDaoException::GetErrorInfo  
 Zwraca informacje o błędzie dotyczących obiektu określony błąd w kolekcji błędów.  
  
```  
void GetErrorInfo(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks informacji o błędach w kolekcji błędów aparatu bazy danych, wyszukiwanie według indeksu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji Członkowskich, aby uzyskać następujące rodzaje informacji o wyjątku:  
  
-   Kod błędu:  
  
-   Źródło  
  
-   Opis  
  
-   Plik pomocy  
  
-   Kontekst pomocy  
  
 `GetErrorInfo` zapisuje informacje w obiekt wyjątku `m_pErrorInfo` element członkowski danych. Krótki opis zwracanych informacji, zobacz [m_pErrorInfo](#m_perrorinfo). Jeśli catch wyjątku typu `CDaoException` zgłoszony przez MFC, `m_pErrorInfo` elementu członkowskiego już zostać wypełnione. Jeśli wybierzesz wywoływanie obiektów DAO bezpośrednio, należy wywołać obiekt wyjątku `GetErrorInfo` funkcji członkowskiej samodzielnie, aby wypełnić `m_pErrorInfo`. Aby uzyskać bardziej szczegółowy opis, zobacz [cdaoerrorinfo —](../../mfc/reference/cdaoerrorinfo-structure.md) struktury.  
  
 Informacje o wyjątki DAO i przykładowy kod, zobacz artykuł [wyjątki: wyjątki bazy danych](../../mfc/exceptions-database-exceptions.md).  
  
##  <a name="m_nafxdaoerror"></a>  CDaoException::m_nAfxDaoError  
 Zawiera MFC, rozszerzony kod błędu.  
  
### <a name="remarks"></a>Uwagi  
 Ten kod jest dostarczany w przypadkach, gdy ma erred określonego składnika klas MFC DAO.  
  
 Możliwe wartości to:  
  
- **NO_AFX_DAO_ERROR** ostatniej operacji nie powoduje błąd rozszerzony MFC. Jednak operacji można tworzą inne błędy z DAO lub OLE, dlatego należy sprawdzić, [m_pErrorInfo](#m_perrorinfo) i prawdopodobnie [m_scode](#m_scode).  
  
- **AFX_DAO_ERROR_ENGINE_INITIALIZATION** MFC nie można zainicjować aparatu bazy danych programu Microsoft Jet. OLE może nie można zainicjować lub było niemożliwe do utworzenia wystąpienia obiektu aparatu bazy danych DAO. Te problemy zwykle sugeruje zły instalacji DAO lub OLE.  
  
- **AFX_DAO_ERROR_DFX_BIND** adres używany w wywołaniu funkcji programu exchange (DFX) pól rekordów DAO nie istnieje lub jest nieprawidłowy (adres nie był używany do wiązania danych). W wywołaniu DFX mogą mieć przekazywane zły adres lub adres może być stały się nieprawidłowa między operacjami DFX.  
  
- **AFX_DAO_ERROR_OBJECT_NOT_OPEN** próbował otworzyć zestaw rekordów na podstawie querydef lub obiektu tabledef, który nie był w stanie otwartym.  
  
##  <a name="m_perrorinfo"></a>  CDaoException::m_pErrorInfo  
 Zawiera wskaźnik do `CDaoErrorInfo` strukturę, która zawiera informacje na temat DAO obiekt błąd, który ostatnio pobranej poprzez wywołanie [GetErrorInfo](#geterrorinfo).  
  
### <a name="remarks"></a>Uwagi  
 Ten obiekt zawiera następujące informacje:  
  
|Cdaoerrorinfo — element członkowski|Informacje|Znaczenie|  
|--------------------------|-----------------|-------------|  
|**m_lErrorCode**|Kod błędu|Kod błędu DAO|  
|`m_strSource`|Źródło|Nazwa obiektu lub aplikacji, która początkowo wygenerował błąd|  
|`m_strDescription`|Opis|Ciąg opisujący skojarzone z powodu błędu|  
|`m_strHelpFile`|Plik pomocy|Ścieżka do pliku Pomocy systemu Windows, w którym użytkownik może uzyskać informacji o problemie|  
|**m_lHelpContext**|Kontekst pomocy|Identyfikator kontekstu dla tematu w pliku pomocy DAO|  
  
 Aby uzyskać szczegółowe informacje o informacje zawarte w `CDaoErrorInfo` obiektów, zobacz [cdaoerrorinfo —](../../mfc/reference/cdaoerrorinfo-structure.md) struktury.  
  
##  <a name="m_scode"></a>  CDaoException::m_scode  
 Zawiera wartość typu `SCODE` opisujący błąd.  
  
### <a name="remarks"></a>Uwagi  
 To jest kod OLE. Rzadko będą musieli używać tej wartości, ponieważ w większości przypadków, jest dostępna w innych bardziej szczegółowe informacje o błędzie MFC lub DAO `CDaoException` elementy członkowskie danych.  
  
 Informacje o `SCODE`, zobacz temat [struktury z OLE kody błędów](http://msdn.microsoft.com/library/windows/desktop/ms690088) w zestawie Windows SDK. `SCODE` Mapowana na typ danych `HRESULT` — typ danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Cexception — klasa](../../mfc/reference/cexception-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CException](../../mfc/reference/cexception-class.md)
