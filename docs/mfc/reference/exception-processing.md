---
title: Przetwarzanie wyjątków
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.exceptions
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
ms.openlocfilehash: 6f74f0fcef7f9dc63138dcdb29487120818974f1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651415"
---
# <a name="exception-processing"></a>Przetwarzanie wyjątków

Liczba nietypowych warunków błędów oraz nazywany "liczba wyjątków" może wystąpić, gdy program działa. Mogą one zawierać, ilość pamięci, błędy alokacji zasobów i nie można odnaleźć plików.

Biblioteki klas Microsoft Foundation używa schematu obsługi wyjątków jest modelowane dokładnie jeden proponowanych przez Komitetu standardów ANSI dla języka C++. Zanim wywołanie funkcji, które mogą wystąpić anormalnej sytuacji można skonfigurować do obsługi wyjątku. Jeśli funkcja napotka warunek nietypowe, występuje wyjątek, a kontrola jest przekazywana do obsługi wyjątków.

Makra kilka dołączonej bibliotece klas Microsoft Foundation zostaną skonfigurowane obsługi wyjątków. Wiele innych funkcji globalnych ułatwiają zgłaszają Wyjątki specjalistyczne, a następnie Zakończ działanie programów, jeśli to konieczne. Te makra i funkcje globalne można podzielić na następujące kategorie:

- Makra wyjątków, które struktury programu obsługi wyjątków.

- Exception-throwing funkcji), które generują wyjątki określonych typów.

- Kończenie działania funkcji, które powodują Kończenie działania programu.

Aby uzyskać szczegółowe informacje i przykłady, zobacz artykuł [wyjątki](../../mfc/exception-handling-in-mfc.md).

### <a name="exception-macros"></a>Makra wyjątków

|||
|-|-|
|[WYPRÓBUJ](#try)|Wskazuje blok kodu do przetwarzania wyjątku.|
|[CATCH](#catch)|Wskazuje blok kodu dla przechwytywanie wyjątku z poprzednim **SPRÓBUJ** bloku.|
|[CATCH_ALL](#catch_all)|Wskazuje blok kodu dla wszystkich wyjątków opisanej w kroku Przechwytywanie **SPRÓBUJ** bloku.|
|[AND_CATCH](#and_catch)|Wskazuje blok kodu dla typów wyjątków dodatkowe opisanej w kroku Przechwytywanie **SPRÓBUJ** bloku.|
|[AND_CATCH_ALL](#and_catch_all)|Wskazuje blok kodu dla wszystkich pozostałych typów dodatkowe wyjątek zgłaszany w kroku Przechwytywanie **SPRÓBUJ** bloku.|
|[END_CATCH](#end_catch)|Kończy się w ciągu ostatnich **CATCH** lub **AND_CATCH** bloku kodu.|
|[END_CATCH_ALL](#end_catch_all)|Kończy się w ciągu ostatnich **CATCH_ALL** bloku kodu.|
|[THROW](#throw)|Generuje określony wyjątek.|
|[THROW_LAST](#throw_last)|Zgłasza aktualnie obsługiwany wyjątek do następnego zewnętrznego programu obsługi.|

### <a name="exception-throwing-functions"></a>Funkcje Wyrzucające

|||
|-|-|
|[Afxthrowarchiveexception —](#afxthrowarchiveexception)|Zgłasza wyjątek archiwum.|
|[Afxthrowfileexception —](#afxthrowfileexception)|Zgłasza wyjątek plików.|
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|Zgłasza wyjątek nieprawidłowego argumentu.|
|[Afxthrowmemoryexception —](#afxthrowmemoryexception)|Zgłasza wyjątek pamięci.|
|[Afxthrownotsupportedexception —](#afxthrownotsupportedexception)|Zgłasza wyjątek nieobsługiwane.|
|[Afxthrowresourceexception —](#afxthrowresourceexception)|Zgłasza wyjątek zasobu nie można odnaleźć Windows.|
|[Afxthrowuserexception —](#afxthrowuserexception)|Zgłasza wyjątek w działaniu programu zainicjowanego przez użytkownika.|

Biblioteka MFC zawiera dwie funkcje wyrzucające wyjątki OLE specjalnie z myślą:

### <a name="ole-exception-functions"></a>Funkcje wyjątek OLE

|||
|-|-|
|[Afxthrowoledispatchexception —](#afxthrowoledispatchexception)|Zgłasza wyjątek w funkcji automatyzacji OLE.|
|[Afxthrowoleexception —](#afxthrowoleexception)|Zgłasza wyjątek OLE.|

Aby obsługiwać wyjątki bazy danych, klasy bazy danych zapewniają dwie klasy wyjątku, `CDBException` i `CDaoException`i funkcje globalne do obsługi typów wyjątków:

### <a name="dao-exception-functions"></a>Funkcje wyjątek DAO

|||
|-|-|
|[Afxthrowdaoexception —](#afxthrowdaoexception)|Zgłasza [CDaoException](../../mfc/reference/cdaoexception-class.md) z własnego kodu.|
|[Afxthrowdbexception —](#afxthrowdbexception)|Zgłasza [CDBException](../../mfc/reference/cdbexception-class.md) z własnego kodu.|

Biblioteka MFC zawiera następującą funkcję zakończenia:

### <a name="termination-functions"></a>Funkcje zakończenia

|||
|-|-|
|[Afxabort —](#afxabort)|Wywołuje się, aby zakończyć aplikację, jeśli błąd krytyczny występuje.|

##  <a name="try"></a>  WYPRÓBUJ

Konfiguruje **SPRÓBUJ** bloku.

```
TRY
```

### <a name="remarks"></a>Uwagi

A **SPRÓBUJ** bloku określa blok kodu, który może zgłaszać wyjątki. Te wyjątki są obsługiwane w następujących **CATCH** i **AND_CATCH** bloków. Rekursja jest dozwolony: wyjątki mogą być przekazywane do zewnętrznego **SPRÓBUJ** bloku, odrzucając je lub za pomocą THROW_LAST — makro. Koniec **SPRÓBUJ** blok z END_CATCH lub END_CATCH_ALL — makro.

Aby uzyskać więcej informacji, zobacz artykuł [wyjątki](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Przykład

Zobacz przykład [CATCH](#catch).

### <a name="requirements"></a>Wymagania

Nagłówek: afx.h

##  <a name="catch"></a>  CATCH

Definiuje bloku kodu, który przechwytuje pierwszy typ wyjątek zgłoszony w poprzednim **SPRÓBUJ** bloku.

```
CATCH(exception_class, exception_object_pointer_name)

```

### <a name="parameters"></a>Parametry

*exception_class*<br/>
Określa typ wyjątku do testowania. Aby uzyskać listę klas standardowych wyjątków, zobacz klasy [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Określa nazwę wskaźnika obiektu wyjątku, który zostanie utworzony przez makro. Można użyć nazwy wskaźnika do dostępu do obiektu wyjątku w ramach **CATCH** bloku. Ta zmienna jest zadeklarowana za Ciebie.

### <a name="remarks"></a>Uwagi

Przetwarzanie wyjątków kod może interrogate obiekt wyjątku, jeśli to stosowne uzyskać więcej informacji na temat określonych Przyczyna wyjątku. Wywołaj THROW_LAST — makro do przesunięcia przetwarzania następnej ramki Wyjątek zewnętrzny. Koniec **SPRÓBUJ** blok z END_CATCH — makro.

Jeśli *exception_class* jest klasą `CException`, a następnie wszystkie typy wyjątków, który zostanie przechwycony. Możesz użyć [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof) funkcja elementu członkowskiego, aby określić, które określony wyjątek został zgłoszony. Lepszy sposób, aby przechwycić kilka rodzajów wyjątków jest użycie sekwencyjne **AND_CATCH** instrukcji, każdy z innego typu wyjątku.

Wskaźnik do obiektu wyjątku jest tworzony przez makra. Nie trzeba deklarować samodzielnie.

> [!NOTE]
>  **CATCH** bloku jest zdefiniowany jako zakres C++ umieszczony w nawiasach klamrowych. Deklarowanie zmiennych, w tym zakresie, jest ona dostępna tylko w tym zakresie. Dotyczy to również *exception_object_pointer_name*.

Aby uzyskać więcej informacji na wyjątki i makra CATCH, zobacz artykuł [wyjątki](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

##  <a name="catch_all"></a>  CATCH_ALL

Definiuje bloku kodu, który przechwytuje wszystkich typów wyjątków zgłoszonych w poprzednim **SPRÓBUJ** bloku.

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_object_pointer_name*<br/>
Określa nazwę wskaźnika obiektu wyjątku, który zostanie utworzony przez makro. Można użyć nazwy wskaźnika do dostępu do obiektu wyjątku w ramach `CATCH_ALL` bloku. Ta zmienna jest zadeklarowana za Ciebie.

### <a name="remarks"></a>Uwagi

Przetwarzanie wyjątków kod może interrogate obiekt wyjątku, jeśli to stosowne uzyskać więcej informacji na temat określonych Przyczyna wyjątku. Wywoływanie `THROW_LAST` makra, aby przesunąć przetwarzania następnej ramki Wyjątek zewnętrzny. Jeśli używasz **CATCH_ALL**, zakończenia **SPRÓBUJ** blok z END_CATCH_ALL — makro.

> [!NOTE]
>  **CATCH_ALL** bloku jest zdefiniowany jako zakres C++ umieszczony w nawiasach klamrowych. Deklarowanie zmiennych, w tym zakresie, jest ona dostępna tylko w tym zakresie.

Aby uzyskać więcej informacji na temat wyjątków, zobacz artykuł [wyjątki](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Przykład

Zobacz przykład [CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

##  <a name="and_catch"></a>  AND_CATCH

Definiuje blok kodu dla Przechwytywanie typów dodatkowe wyjątek zgłoszony w poprzednich **SPRÓBUJ** bloku.

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_class*<br/>
Określa typ wyjątku do testowania. Aby uzyskać listę klas standardowych wyjątków, zobacz klasy [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Nazwa wskaźnika obiektu wyjątku, który zostanie utworzony przez makro. Można użyć nazwy wskaźnika do dostępu do obiektu wyjątku w ramach **AND_CATCH** bloku. Ta zmienna jest zadeklarowana za Ciebie.

### <a name="remarks"></a>Uwagi

Użyj makra CATCH do przechwytywania jeden typ wyjątku, a następnie AND_CATCH — makro, aby przechwycić każdego typu kolejne. Koniec **SPRÓBUJ** blok z END_CATCH — makro.

Przetwarzanie wyjątków kod może interrogate obiekt wyjątku, jeśli to stosowne uzyskać więcej informacji na temat określonych Przyczyna wyjątku. Wywołaj THROW_LAST — makro w ramach **AND_CATCH** shift przetwarzania do następnej ramki Wyjątek zewnętrzny za pomocą bloku. **AND_CATCH** oznacza koniec poprzedniego **CATCH** lub **AND_CATCH** bloku.

> [!NOTE]
>  **AND_CATCH** bloku jest zdefiniowany jako zakres C++ (umieszczony w nawiasy klamrowe). Deklarowanie zmiennych, w tym zakresie, należy pamiętać, że są one dostępne tylko w tym zakresie. Dotyczy to również *exception_object_pointer_name* zmiennej.

### <a name="example"></a>Przykład

Zobacz przykład [CATCH](#catch).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h
##  <a name="and_catch_all"></a>  AND_CATCH_ALL

Definiuje blok kodu dla Przechwytywanie typów dodatkowe wyjątek zgłoszony w poprzednich **SPRÓBUJ** bloku.

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_object_pointer_name*<br/>
Nazwa wskaźnika obiektu wyjątku, który zostanie utworzony przez makro. Można użyć nazwy wskaźnika do dostępu do obiektu wyjątku w ramach **AND_CATCH_ALL** bloku. Ta zmienna jest zadeklarowana za Ciebie.

### <a name="remarks"></a>Uwagi

Użyj **CATCH** makra, aby jeden typ wyjątku, a następnie AND_CATCH_ALL — makro w celu przechwytywania wszystkich pozostałych typów kolejne. Jeśli używasz AND_CATCH_ALL, **SPRÓBUJ** blok z END_CATCH_ALL — makro.

Przetwarzanie wyjątków kod może interrogate obiekt wyjątku, jeśli to stosowne uzyskać więcej informacji na temat określonych Przyczyna wyjątku. Wywołaj THROW_LAST — makro w ramach **AND_CATCH_ALL** shift przetwarzania do następnej ramki Wyjątek zewnętrzny za pomocą bloku. **AND_CATCH_ALL** oznacza koniec poprzedniego **CATCH** lub **AND_CATCH_ALL** bloku.

> [!NOTE]
>  **AND_CATCH_ALL** bloku jest zdefiniowany jako zakres C++ (umieszczony w nawiasach klamrowych). Deklarowanie zmiennych, w tym zakresie, należy pamiętać, że są one dostępne tylko w tym zakresie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

##  <a name="end_catch"></a>  END_CATCH

Oznacza koniec ostatnich **CATCH** lub **AND_CATCH** bloku.

```
END_CATCH
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat END_CATCH — makro, zobacz artykuł [wyjątki](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

##  <a name="end_catch_all"></a>  END_CATCH_ALL

Oznacza koniec ostatnich ** CATCH_ALL88 lub **AND_CATCH_ALL** bloku.

```
END_CATCH_ALL
```

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

##  <a name="throw"></a>  THROW (MFC)

Określony wyjątek.

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>Parametry

*exception_object_pointer*<br/>
Wskazuje na obiekt wyjątku pochodną `CException`.

### <a name="remarks"></a>Uwagi

**THROW** wykonywanie, przekazując kontrolę do skojarzonego programu do przerwania **CATCH** Blokuj w programie. Jeśli nie podano **CATCH** zablokować, a następnie sterowanie jest przekazywane do modułu bibliotekę Microsoft Foundation Class, który wyświetla błąd komunikat i kończy działanie.

Aby uzyskać więcej informacji, zobacz artykuł [wyjątki](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

##  <a name="throw_last"></a>  THROW_LAST

Zgłasza wyjątek z powrotem do następnego zewnętrzne **CATCH** bloku.

```
THROW_LAST()
```

### <a name="remarks"></a>Uwagi

To makro umożliwia zgłoszenie wyjątku utworzone lokalnie. Jeśli zostanie podjęta próba zgłosić wyjątek, który ma tylko przechwycony, zwykle będzie wykraczają poza zakres i go usunąć. Za pomocą **THROW_LAST**, wyjątek jest poprawnie przekazywany do następnego **CATCH** programu obsługi.

Aby uzyskać więcej informacji, zobacz artykuł [wyjątki](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Przykład

Zobacz przykład [CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

##  <a name="afxthrowarchiveexception"></a>  Afxthrowarchiveexception —

Zgłasza wyjątek archiwum.

```
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>Parametry

*Przyczyna*<br/>
Określa całkowitą, która wskazuje przyczynę, dla wyjątku. Aby uzyskać listę możliwych wartości, zobacz [CArchiveException::m_cause](../../mfc/reference/carchiveexception-class.md#m_cause).

*lpszArchiveName*<br/>
Wskazuje ciąg zawierający nazwę `CArchive` obiektu, który spowodował wyjątek (jeśli jest dostępny).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

##  <a name="afxthrowfileexception"></a>  Afxthrowfileexception —

Zgłasza wyjątek plików.

```
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parametry

*Przyczyna*<br/>
Określa całkowitą, która wskazuje przyczynę, dla wyjątku. Aby uzyskać listę możliwych wartości, zobacz [CFileException::m_cause](../../mfc/reference/cfileexception-class.md#m_cause).

*lOsError*<br/>
Zawiera numer błędu systemu operacyjnego (jeśli jest dostępny), Stany Przyczyna, dla wyjątku. Znaleźć w podręczniku użytkownika systemu operacyjnego, aby uzyskać listę kodów błędów.

*lpszFileName*<br/>
Wskazuje ciąg zawierający nazwę pliku, który spowodował wyjątek (jeśli jest dostępny).

### <a name="remarks"></a>Uwagi

Odpowiedzialność za ustalenie jego przyczyny, w oparciu o kod błędu systemu operacyjnego.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

## <a name="afxthrowinvalidargexception"></a>  AfxThrowInvalidArgException

Zgłasza wyjątek nieprawidłowego argumentu.

### <a name="syntax"></a>Składnia

```
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana, gdy używane są nieprawidłowe argumenty.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

### <a name="see-also"></a>Zobacz też

[Makra i funkcje globalne](mfc-macros-and-globals.md)<br/>
[Klasa CInvalidArgException](cinvalidargexception-class.md)<br/>
[THROW](#throw)

##  <a name="afxthrowmemoryexception"></a>  Afxthrowmemoryexception —

Zgłasza wyjątek pamięci.

```
void AfxThrowMemoryException();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, jeśli wywołania do bazowego buforów pamięci systemu (takich jak **— funkcja malloc** i [działanie funkcji GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) funkcji Windows) się nie powieść. Nie musisz wywołać ją dla **nowe** ponieważ **nowe** spowoduje zgłoszenie wyjątku pamięci automatycznie Jeśli alokacja pamięci nie powiedzie się.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

##  <a name="afxthrownotsupportedexception"></a>  Afxthrownotsupportedexception —

Zgłasza wyjątek, który jest wynikiem żądania nieobsługiwanej funkcji.

```
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

##  <a name="afxthrowresourceexception"></a>  Afxthrowresourceexception —

Wyjątek zasobu.

```
void  AfxThrowResourceException();
```

### <a name="remarks"></a>Uwagi

Ta funkcja zwykle jest wywoływana, gdy nie można załadować zasobu Windows.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

##  <a name="afxthrowuserexception"></a>  Afxthrowuserexception —

Zgłasza wyjątek, aby zatrzymać operacje użytkownika końcowego.

```
void AfxThrowUserException();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest zazwyczaj wywoływana bezpośrednio po `AfxMessageBox` zgłosił błąd dla użytkownika.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

##  <a name="afxthrowoledispatchexception"></a>  Afxthrowoledispatchexception —

Ta funkcja umożliwia zgłoszenie wyjątku w funkcji automatyzacji OLE.

```
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

*Wcode —*<br/>
Kod błędu określony dla twojej aplikacji.

*lpszDescription*<br/>
Ustne opis błędu.

*nDescriptionID*<br/>
Identyfikator zasobu opisu błędu pisemnych.

*nHelpID*<br/>
Kontekstu pomocy w celu uzyskania pomocy w aplikacji (. Plik HLP).

### <a name="remarks"></a>Uwagi

Informacje podane w tej funkcji mogą być wyświetlane przez aplikację jazdy (Microsoft Visual Basic lub innej aplikacji automatyzacji OLE).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

##  <a name="afxthrowoleexception"></a>  Afxthrowoleexception —

Tworzy obiekt typu `COleException` i zgłasza wyjątek.

```
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>Parametry

*sc*<br/>
Kod stanu OLE, która wskazuje przyczynę wyjątku.

*godz.*<br/>
Dojście do kod wyniku, który wskazuje przyczyny, dla wyjątku.

### <a name="remarks"></a>Uwagi

Wersja, która przyjmuje wartość HRESULT jako argument konwertuje kod wyniku odpowiedniego SCODE. Aby uzyskać więcej informacji na temat HRESULT i SCODE, zobacz [struktury COM kody błędów](/windows/desktop/com/structure-of-com-error-codes) w zestawie Windows SDK.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

##  <a name="afxthrowdaoexception"></a>  Afxthrowdaoexception —

Wywołaj tę funkcję, aby zgłosić wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md) z własnego kodu.

```
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>Parametry

*nAfxDaoError*<br/>
Wartość całkowitą reprezentującą DAO, rozszerzony kod błędu, które mogą być jedna z wartości wyświetlane w obszarze [CDaoException::m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror).

*scode*<br/>
Kod błędu OLE z DAO typu SCODE. Aby uzyskać informacje, zobacz [CDaoException::m_scode](../../mfc/reference/cdaoexception-class.md#m_scode).

### <a name="remarks"></a>Uwagi

Struktura również wywołuje `AfxThrowDaoException`. W swojej rozmowy można przekazać jeden z parametrów lub obu. Na przykład, jeśli chcesz wywołać jedną z błędy są zdefiniowane w **CDaoException::nAfxDaoError** , ale nie interesujące Cię *scode* parametru, Przekaż prawidłowy kod w *nAfxDaoError* parametru i zaakceptuj wartość domyślną dla *scode*.

Dla informacji dotyczących wyjątków związanych z klas MFC DAO, zobacz klasę `CDaoException` w tej książce i artykuł [wyjątki: wyjątki bazy danych](../../mfc/exceptions-database-exceptions.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdb.h

##  <a name="afxthrowdbexception"></a>  Afxthrowdbexception —

Wywołaj tę funkcję, aby zgłosić wyjątek typu `CDBException` z własnego kodu.

```
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*nRetCode*<br/>
Wartości typu RETCODE, definiujący typ błędu, który spowodował zgłoszenie wyjątku.

*plik PDB*<br/>
Wskaźnik do `CDatabase` obiekt, który reprezentuje połączenie źródła danych, z którym skojarzony jest wyjątek.

*hstmt*<br/>
Dojście ODBC HSTMT, określający dojście instrukcji, z którym skojarzony jest wyjątek.

### <a name="remarks"></a>Uwagi

Struktura wywołuje `AfxThrowDBException` kiedy odbierze RETCODE ODBC z wywołania do funkcji interfejsu API ODBC i interpretuje RETCODE wyjątkowy warunek zamiast expectable błąd. Na przykład operacja dostępu do danych może zakończyć się niepowodzeniem ze względu na błąd odczytu z dysku.

Informacje o wartości RETCODE zdefiniowanych przez ODBC znajduje się rozdział 8, "Trwa pobieranie stanu oraz informacje o błędzie," w zestawie Windows SDK. Informacje na temat rozszerzeń MFC do tych kodów, zawiera klasa [CDBException](../../mfc/reference/cdbexception-class.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

##  <a name="afxabort"></a>  Afxabort —

Zakończenie domyślnej funkcji, dostarczonych przez MFC.

```
void  AfxAbort();
```

### <a name="remarks"></a>Uwagi

`AfxAbort` jest wywoływana wewnętrznie przez funkcje składowe MFC po błąd krytyczny, takich jak nieprzechwycony wyjątek, który nie może być obsługiwane. Możesz wywołać `AfxAbort` w rzadkich przypadkach, w przypadku wystąpienia błędu krytycznego, z którego nie można odzyskać.

### <a name="example"></a>Przykład

Zobacz przykład [CATCH](#catch).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

## <a name="see-also"></a>Zobacz też

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[Klasa CException](../../mfc/reference/cexception-class.md)
