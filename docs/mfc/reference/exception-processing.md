---
title: Przetwarzanie wyjątków
ms.date: 11/04/2016
helpviewer_keywords:
- macros [MFC], exception handling
- DAO (Data Access Objects), exceptions [MFC]
- OLE exceptions [MFC], MFC functions
- exceptions [MFC], processing
- exception macros [MFC]
- termination functions, MFC
- MFC, exceptions
- exceptions [MFC], MFC throwing functions
ms.assetid: 26d4457c-8350-48f5-916e-78f919787c30
ms.openlocfilehash: 9d6a1c30ca0811085124a5fb5994c5f35d412ae7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837192"
---
# <a name="exception-processing"></a>Przetwarzanie wyjątków

Gdy program jest wykonywany, może wystąpić wiele nietypowych warunków i błędów o nazwie "Exceptions". Mogą one obejmować Brak pamięci, błędy alokacji zasobów i niepowodzenie wyszukiwania plików.

Biblioteka MFC używa schematu obsługi wyjątków, który jest dobrze odwzorowany po zaproponowaniu przez Komitet standardów ANSI dla języka C++. Program obsługi wyjątków musi zostać skonfigurowany przed wywołaniem funkcji, która może wystąpić w nietypowej sytuacji. Jeśli funkcja napotka nietypowy warunek, zgłasza wyjątek, a kontrola jest przenoszona do procedury obsługi wyjątków.

Kilka makr zawartych w biblioteka MFC skonfiguruje obsługę wyjątków. Niektóre inne funkcje globalne pomagają generować wyspecjalizowane wyjątki i kończyć programy, w razie potrzeby. Te makra i funkcje globalne mieszczą się w następujących kategoriach:

- Makra wyjątków, które są strukturą programu obsługi wyjątków.

- Funkcje zgłaszania wyjątków), które generują wyjątki dla określonych typów.

- Funkcje kończenia, które powodują zakończenie działania programu.

Aby zapoznać się z przykładami i więcej szczegółów, zobacz [wyjątki](../../mfc/exception-handling-in-mfc.md)w artykule.

### <a name="exception-macros"></a>Makra wyjątków

|Nazwa|Opis|
|-|-|
|[SPRÓBOWAŁ](#try)|Określa blok kodu do przetwarzania wyjątków.|
|[EFEKTYWN](#catch)|Określa blok kodu do przechwytywania wyjątku z poprzedniego bloku **try** .|
|[CATCH_ALL](#catch_all)|Określa blok kodu do przechwytywania wszystkich wyjątków z poprzedniego bloku **try** .|
|[AND_CATCH](#and_catch)|Określa blok kodu do przechwytywania dodatkowych typów wyjątków z poprzedniego bloku **try** .|
|[AND_CATCH_ALL](#and_catch_all)|Określa blok kodu do przechwytywania wszystkich innych dodatkowych typów wyjątków zgłoszonych w poprzednim bloku **try** .|
|[END_CATCH](#end_catch)|Zamyka ostatni blok kodu **catch** lub **AND_CATCH** .|
|[END_CATCH_ALL](#end_catch_all)|Zamyka ostatni **CATCH_ALL** bloku kodu.|
|[GENEROWAĆ](#throw)|Zgłasza określony wyjątek.|
|[THROW_LAST](#throw_last)|Zgłasza aktualnie obsługiwany wyjątek do następnej zewnętrznej procedury obsługi.|

### <a name="exception-throwing-functions"></a>Funkcje zgłaszania wyjątków

|Nazwa|Opis|
|-|-|
|[AfxThrowArchiveException](#afxthrowarchiveexception)|Zgłasza wyjątek archiwum.|
|[AfxThrowFileException](#afxthrowfileexception)|Zgłasza wyjątek pliku.|
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|Zgłasza wyjątek nieprawidłowego argumentu.|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|Zgłasza wyjątek pamięci.|
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|Zgłasza wyjątek nieobsługiwany.|
|[AfxThrowResourceException](#afxthrowresourceexception)|Zgłasza wyjątek Nieznaleziono zasobu systemu Windows.|
|[AfxThrowUserException](#afxthrowuserexception)|Zgłasza wyjątek w akcji programu zainicjowanej przez użytkownika.|

MFC oferuje dwie funkcje zgłaszania wyjątków dla wyjątków OLE:

### <a name="ole-exception-functions"></a>Funkcje wyjątków OLE

|Nazwa|Opis|
|-|-|
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|Zgłasza wyjątek w funkcji automatyzacji OLE.|
|[AfxThrowOleException](#afxthrowoleexception)|Zgłasza wyjątek OLE.|

W celu zapewnienia obsługi wyjątków bazy danych klasy baz danych udostępniają dwie klasy wyjątków `CDBException` oraz `CDaoException` funkcje globalne obsługujące typy wyjątków:

### <a name="dao-exception-functions"></a>Funkcje wyjątków DAO

|Nazwa|Opis|
|-|-|
|[AfxThrowDAOException](#afxthrowdaoexception)|Zgłasza [CDaoException](../../mfc/reference/cdaoexception-class.md) z własnego kodu.|
|[AfxThrowDBException](#afxthrowdbexception)|Zgłasza [CDBException](../../mfc/reference/cdbexception-class.md) z własnego kodu.|

MFC zapewnia następującą funkcję zakończenia:

### <a name="termination-functions"></a>Funkcje zakończenia

|Nazwa|Opis|
|-|-|
|[AfxAbort](#afxabort)|Wywołuje się, by przerwać aplikację w przypadku wystąpienia błędu krytycznego.|

## <a name="try"></a><a name="try"></a> SPRÓBOWAŁ

Konfiguruje blok **try** .

```
TRY
```

### <a name="remarks"></a>Uwagi

Blok **try** identyfikuje blok kodu, który może zgłaszać wyjątki. Te wyjątki są obsługiwane w następujących blokach **catch** i **AND_CATCH** . Rekursja jest dozwolona: wyjątki mogą być przesyłane do zewnętrznego bloku **try** , przez ignorowanie ich lub za pomocą makra THROW_LAST. Zakończ blok **try** za pomocą makra END_CATCH lub END_CATCH_ALL.

Aby uzyskać więcej informacji, zobacz [wyjątki](../../mfc/exception-handling-in-mfc.md)w artykule.

### <a name="example"></a>Przykład

Zobacz przykład [przechwytywania](#catch).

### <a name="requirements"></a>Wymagania

Nagłówek: AFX. h

## <a name="catch"></a><a name="catch"></a> EFEKTYWN

Definiuje blok kodu, który przechwytuje pierwszy typ wyjątku zgłoszony w poprzednim bloku **try** .

```
CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_class*<br/>
Określa typ wyjątku do przetestowania. Aby uzyskać listę klas wyjątków standardowych, zobacz Klasa [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Określa nazwę wskaźnika obiektu wyjątku, który zostanie utworzony przez makro. Możesz użyć nazwy wskaźnika, aby uzyskać dostęp do obiektu Exception w bloku **catch** . Ta zmienna jest zadeklarowana dla Ciebie.

### <a name="remarks"></a>Uwagi

Kod przetwarzania wyjątków może przejrzeć obiekt wyjątku, jeśli jest to konieczne, aby uzyskać więcej informacji na temat konkretnej przyczyny wyjątku. Wywołaj makro THROW_LAST, aby przesunąć przetwarzanie do następnego zewnętrznego ramki wyjątków. Zakończ blok **try** za pomocą makra END_CATCH.

Jeśli *exception_class* jest klasą `CException` , zostaną przechwycone wszystkie typy wyjątków. Można użyć funkcji składowej [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof) , aby określić, który konkretny wyjątek został zgłoszony. Lepszym sposobem przechwytywania kilku rodzajów wyjątków jest użycie instrukcji **AND_CATCH** sekwencyjnych, z których każdy ma inny typ wyjątku.

Wskaźnik obiektu wyjątku jest tworzony przez makro. Nie musisz zadeklarować go samodzielnie.

> [!NOTE]
> Blok **catch** jest definiowany jako zakres języka C++, który jest zakreślony w nawiasach klamrowych. Jeśli deklarujesz zmienne w tym zakresie, są one dostępne tylko w tym zakresie. Dotyczy to również *exception_object_pointer_name*.

Aby uzyskać więcej informacji o wyjątkach i makro CATCH, zobacz [wyjątki](../../mfc/exception-handling-in-mfc.md)w artykule.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

## <a name="catch_all"></a><a name="catch_all"></a> CATCH_ALL

Definiuje blok kodu, który przechwytuje wszystkie typy wyjątków zgłoszone w poprzednim bloku **try** .

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_object_pointer_name*<br/>
Określa nazwę wskaźnika obiektu wyjątku, który zostanie utworzony przez makro. Możesz użyć nazwy wskaźnika, aby uzyskać dostęp do obiektu wyjątku w `CATCH_ALL` bloku. Ta zmienna jest zadeklarowana dla Ciebie.

### <a name="remarks"></a>Uwagi

Kod przetwarzania wyjątków może przejrzeć obiekt wyjątku, jeśli jest to konieczne, aby uzyskać więcej informacji na temat konkretnej przyczyny wyjątku. Wywołaj `THROW_LAST` makro, aby przesunąć przetwarzanie do następnego zewnętrznego ramki wyjątków. Jeśli używasz **CATCH_ALL**, Zakończ blok **try** za pomocą makra END_CATCH_ALL.

> [!NOTE]
> Blok **CATCH_ALL** jest zdefiniowany jako zakres języka C++, który jest zakreślony przez nawiasy klamrowe. Jeśli deklarujesz zmienne w tym zakresie, są one dostępne tylko w tym zakresie.

Aby uzyskać więcej informacji o wyjątkach, zobacz [wyjątki](../../mfc/exception-handling-in-mfc.md)w artykule.

### <a name="example"></a>Przykład

Zobacz przykład dla [CFile:: Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFX. h

## <a name="and_catch"></a><a name="and_catch"></a> AND_CATCH

Definiuje blok kodu do przechwytywania dodatkowych typów wyjątków zgłoszonych w poprzednim bloku **try** .

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_class*<br/>
Określa typ wyjątku do przetestowania. Aby uzyskać listę klas wyjątków standardowych, zobacz Klasa [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Nazwa wskaźnika obiektu wyjątku, który zostanie utworzony przez makro. Możesz użyć nazwy wskaźnika, aby uzyskać dostęp do obiektu Exception w bloku **AND_CATCH** . Ta zmienna jest zadeklarowana dla Ciebie.

### <a name="remarks"></a>Uwagi

Użyj makra CATCH do przechwytywania jednego typu wyjątku, a następnie makro AND_CATCH, aby przechwycić każdy kolejny typ. Zakończ blok **try** za pomocą makra END_CATCH.

Kod przetwarzania wyjątków może przejrzeć obiekt wyjątku, jeśli jest to konieczne, aby uzyskać więcej informacji na temat konkretnej przyczyny wyjątku. Wywołaj makro THROW_LAST w bloku **AND_CATCH** , aby przesunąć przetwarzanie do następnego zewnętrznego ramki wyjątków. **AND_CATCH** oznacza koniec poprzedniego bloku **catch** lub **AND_CATCH** .

> [!NOTE]
> Blok **AND_CATCH** jest zdefiniowany jako zakres języka C++ (w którym są nakreślone nawiasy klamrowe). Jeśli deklarujesz zmienne w tym zakresie, pamiętaj, że są one dostępne tylko w tym zakresie. Dotyczy to również zmiennej *exception_object_pointer_name* .

### <a name="example"></a>Przykład

Zobacz przykład [przechwytywania](#catch).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFX. h

## <a name="and_catch_all"></a><a name="and_catch_all"></a> AND_CATCH_ALL

Definiuje blok kodu do przechwytywania dodatkowych typów wyjątków zgłoszonych w poprzednim bloku **try** .

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_object_pointer_name*<br/>
Nazwa wskaźnika obiektu wyjątku, który zostanie utworzony przez makro. Możesz użyć nazwy wskaźnika, aby uzyskać dostęp do obiektu Exception w bloku **AND_CATCH_ALL** . Ta zmienna jest zadeklarowana dla Ciebie.

### <a name="remarks"></a>Uwagi

Użyj makra **catch** do przechwytywania jednego typu wyjątku, a następnie makro AND_CATCH_ALL, aby przechwycić wszystkie pozostałe typy. Jeśli używasz AND_CATCH_ALL, Zakończ blok **try** za pomocą makra END_CATCH_ALL.

Kod przetwarzania wyjątków może przejrzeć obiekt wyjątku, jeśli jest to konieczne, aby uzyskać więcej informacji na temat konkretnej przyczyny wyjątku. Wywołaj makro THROW_LAST w bloku **AND_CATCH_ALL** , aby przesunąć przetwarzanie do następnego zewnętrznego ramki wyjątków. **AND_CATCH_ALL** oznacza koniec poprzedniego bloku **catch** lub **AND_CATCH_ALL** .

> [!NOTE]
> Blok **AND_CATCH_ALL** jest zdefiniowany jako zakres języka C++ (z zakreśloną przez nawiasy klamrowe). Jeśli deklarujesz zmienne w tym zakresie, pamiętaj, że są one dostępne tylko w tym zakresie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFX. h

## <a name="end_catch"></a><a name="end_catch"></a> END_CATCH

Oznacza koniec ostatniego bloku **catch** lub **AND_CATCH** .

```
END_CATCH
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat makra END_CATCH, zobacz [wyjątki](../../mfc/exception-handling-in-mfc.md)w artykule.

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFX. h

## <a name="end_catch_all"></a><a name="end_catch_all"></a> END_CATCH_ALL

Oznacza koniec ostatniego bloku **CATCH_ALL88** lub **AND_CATCH_ALL** .

```
END_CATCH_ALL
```

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFX. h

## <a name="throw-mfc"></a><a name="throw"></a> THROW (MFC)

Zgłasza określony wyjątek.

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>Parametry

*exception_object_pointer*<br/>
Wskazuje obiekt wyjątku pochodzący od `CException` .

### <a name="remarks"></a>Uwagi

**Throw** przerywa wykonywanie programu, przekazując kontrolę do skojarzonego bloku **catch** w programie. Jeśli blok **catch** nie został podany, sterowanie jest przekazywane do modułu Biblioteka MFC, który drukuje komunikat o błędzie i kończy działanie.

Aby uzyskać więcej informacji, zobacz [wyjątki](../../mfc/exception-handling-in-mfc.md)w artykule.

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFX. h

## <a name="throw_last"></a><a name="throw_last"></a> THROW_LAST

Zgłasza wyjątek z powrotem do następnego zewnętrznego bloku **catch** .

```
THROW_LAST()
```

### <a name="remarks"></a>Uwagi

To makro pozwala zgłosić wyjątek utworzony lokalnie. Jeśli spróbujesz zgłosić wyjątek, który został właśnie przechwycony, zwykle wyjdzie poza zakres i zostanie usunięty. W przypadku **THROW_LAST**wyjątek jest prawidłowo przenoszona do następnego programu obsługi **catch** .

Aby uzyskać więcej informacji, zobacz [wyjątki](../../mfc/exception-handling-in-mfc.md)w artykule.

### <a name="example"></a>Przykład

Zobacz przykład dla [CFile:: Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFX. h

## <a name="afxthrowarchiveexception"></a><a name="afxthrowarchiveexception"></a> AfxThrowArchiveException

Zgłasza wyjątek archiwum.

```cpp
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>Parametry

*może*<br/>
Określa liczbę całkowitą, która wskazuje przyczynę wyjątku. Aby uzyskać listę możliwych wartości, zobacz [CArchiveException:: m_cause](../../mfc/reference/carchiveexception-class.md#m_cause).

*lpszArchiveName*<br/>
Wskazuje ciąg zawierający nazwę `CArchive` obiektu, który spowodował wyjątek (jeśli jest dostępny).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFX. h

## <a name="afxthrowfileexception"></a><a name="afxthrowfileexception"></a> AfxThrowFileException

Zgłasza wyjątek pliku.

```cpp
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parametry

*może*<br/>
Określa liczbę całkowitą, która wskazuje przyczynę wyjątku. Aby uzyskać listę możliwych wartości, zobacz [CFileException:: m_cause](../../mfc/reference/cfileexception-class.md#m_cause).

*lOsError*<br/>
Zawiera numer błędu systemu operacyjnego (jeśli jest dostępny), który wskazuje przyczynę wyjątku. Zapoznaj się z instrukcją systemu operacyjnego, aby zapoznać się z listą kodów błędów.

*lpszFileName*<br/>
Wskazuje ciąg zawierający nazwę pliku, który spowodował wyjątek (jeśli jest dostępny).

### <a name="remarks"></a>Uwagi

Użytkownik jest odpowiedzialny za określenie przyczyny na podstawie kodu błędu systemu operacyjnego.

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFX. h

## <a name="afxthrowinvalidargexception"></a><a name="afxthrowinvalidargexception"></a> AfxThrowInvalidArgException

Zgłasza wyjątek nieprawidłowego argumentu.

### <a name="syntax"></a>Składnia

```cpp
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana, gdy są używane nieprawidłowe argumenty.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

## <a name="afxthrowmemoryexception"></a><a name="afxthrowmemoryexception"></a> AfxThrowMemoryException

Zgłasza wyjątek pamięci.

```cpp
void AfxThrowMemoryException();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, jeśli wywołania alokacji podstawowych pamięci systemowej (takie jak **malloc** i funkcja [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) systemu Windows) kończą się niepowodzeniem. Nie musisz go wywoływać, **`new`** ponieważ spowoduje to **`new`** automatyczne zgłoszenie wyjątku pamięci, jeśli alokacja pamięci nie powiedzie się.

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFX. h

## <a name="afxthrownotsupportedexception"></a><a name="afxthrownotsupportedexception"></a> AfxThrowNotSupportedException

Zgłasza wyjątek, który jest wynikiem żądania nieobsługiwanej funkcji.

```cpp
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFX. h

## <a name="afxthrowresourceexception"></a><a name="afxthrowresourceexception"></a> AfxThrowResourceException

Zgłasza wyjątek zasobu.

```cpp
void  AfxThrowResourceException();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest zwykle wywoływana, gdy nie można załadować zasobu systemu Windows.

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFX. h

## <a name="afxthrowuserexception"></a><a name="afxthrowuserexception"></a> AfxThrowUserException

Zgłasza wyjątek, aby zatrzymać operację użytkownika końcowego.

```cpp
void AfxThrowUserException();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest zwykle wywoływana natychmiast po `AfxMessageBox` zgłoszeniu błędu użytkownikowi.

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFX. h

## <a name="afxthrowoledispatchexception"></a><a name="afxthrowoledispatchexception"></a> AfxThrowOleDispatchException

Użyj tej funkcji, aby zgłosić wyjątek w funkcji automatyzacji OLE.

```cpp
void AFXAPI AfxThrowOleDispatchException(
    WORD wCode ,
    LPCSTR lpszDescription,
    UINT nHelpID = 0);

void AFXAPI AfxThrowOleDispatchException(
    WORD wCode,
    UINT nDescriptionID,
    UINT nHelpID = -1);
```

### <a name="parameters"></a>Parametry

*Kodostrzeżenia*<br/>
Kod błędu specyficzny dla aplikacji.

*lpszDescription*<br/>
Werbalny opis błędu.

*nDescriptionID*<br/>
Identyfikator zasobu dla przykładowego opisu błędu.

*nHelpID*<br/>
Kontekst pomocy dla pomocy aplikacji (. HLP).

### <a name="remarks"></a>Uwagi

Informacje dostępne dla tej funkcji mogą być wyświetlane przez aplikację do obsługi (Microsoft Visual Basic lub inną aplikację kliencką OLE Automation).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFX. h

## <a name="afxthrowoleexception"></a><a name="afxthrowoleexception"></a> AfxThrowOleException

Tworzy obiekt typu `COleException` i zgłasza wyjątek.

```cpp
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>Parametry

*polecenia*<br/>
Kod stanu OLE, który wskazuje przyczynę wyjątku.

*godz.*<br/>
Dojście do kodu wyniku, który wskazuje przyczynę wyjątku.

### <a name="remarks"></a>Uwagi

Wersja, która przyjmuje wynik HRESULT jako argument konwertuje ten kod wyniku na odpowiedni SCODE. Aby uzyskać więcej informacji na temat HRESULT i SCODE, zobacz [struktury kodów błędów modelu COM](/windows/win32/com/structure-of-com-error-codes) w Windows SDK.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao. h

## <a name="afxthrowdaoexception"></a><a name="afxthrowdaoexception"></a> AfxThrowDaoException

Wywołaj tę funkcję, aby zgłosić wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md) z własnego kodu.

```cpp
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>Parametry

*nAfxDaoError*<br/>
Wartość całkowita reprezentująca rozszerzony kod błędu obiektu DAO, który może być jedną z wartości wymienionych w obszarze [CDaoException:: m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror).

*SCODE*<br/>
Kod błędu OLE z obiektu DAO typu SCODE. Aby uzyskać więcej informacji, zobacz [CDaoException:: m_scode](../../mfc/reference/cdaoexception-class.md#m_scode).

### <a name="remarks"></a>Uwagi

Struktura również wywołuje `AfxThrowDaoException` . W wywołaniu można przekazać jeden z parametrów lub oba te parametry. Na przykład jeśli chcesz zgłosić jeden z błędów zdefiniowanych w **CDaoException:: nAfxDaoError** , ale nie chcesz zachować tego parametru *SCODE* , Przekaż prawidłowy kod w parametrze *nAfxDaoError* i Zaakceptuj wartość domyślną dla *SCODE*.

Aby uzyskać informacje dotyczące wyjątków związanych z klasami MFC DAO, zobacz Klasa `CDaoException` w tej książce i [wyjątki artykułów: wyjątki bazy danych](../../mfc/exceptions-database-exceptions.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDB. h

## <a name="afxthrowdbexception"></a><a name="afxthrowdbexception"></a> AfxThrowDBException

Wywołaj tę funkcję, aby zgłosić wyjątek typu `CDBException` z własnego kodu.

```cpp
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*nRetCode*<br/>
Wartość typu RETCODE, definiująca typ błędu, który spowodował zgłoszenie wyjątku.

*PDB*<br/>
Wskaźnik do `CDatabase` obiektu, który reprezentuje połączenie ze źródłem danych, z którym jest skojarzony wyjątek.

*hstmt*<br/>
Uchwyt HSTMT ODBC, który określa uchwyt instrukcji, z którym jest skojarzony wyjątek.

### <a name="remarks"></a>Uwagi

Struktura wywołuje, `AfxThrowDBException` kiedy otrzymuje ODBC RETCODE z wywołania funkcji ODBC API i interpretuje RETCODE jako wyjątkowy warunek, a nie oczekiwany błąd. Na przykład operacja dostępu do danych może zakończyć się niepowodzeniem z powodu błędu odczytu dysku.

Aby uzyskać informacje o wartościach RETCODE zdefiniowanych przez ODBC, zobacz rozdział 8 "Pobieranie stanu i informacji o błędach" w Windows SDK. Aby uzyskać informacje na temat rozszerzeń MFC do tych kodów, zobacz Class [CDBException](../../mfc/reference/cdbexception-class.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFX. h

## <a name="afxabort"></a><a name="afxabort"></a> AfxAbort

Domyślna funkcja zakończenia dostarczana przez MFC.

```cpp
void  AfxAbort();
```

### <a name="remarks"></a>Uwagi

`AfxAbort` jest wywoływana wewnętrznie przez funkcje składowe MFC w przypadku wystąpienia błędu krytycznego, takiego jak nieprzechwycony wyjątek, którego nie można obsłużyć. Można wywołać `AfxAbort` w rzadkim przypadku, gdy wystąpi błąd krytyczny, z którego nie można przeprowadzić odzyskiwania.

### <a name="example"></a>Przykład

Zobacz przykład [przechwytywania](#catch).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFX. h

## <a name="see-also"></a>Zobacz też

[Makra i Globals](mfc-macros-and-globals.md)<br/>
[Klasa CException](cexception-class.md)<br/>
[Klasa CInvalidArgException](cinvalidargexception-class.md)
