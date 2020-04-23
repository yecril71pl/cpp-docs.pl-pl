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
ms.openlocfilehash: bdf9dee88c29621bdc77c83d2633d93b4b9d10a7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751612"
---
# <a name="exception-processing"></a>Przetwarzanie wyjątków

Podczas wykonywania programu może wystąpić szereg nietypowych warunków i błędów nazywanych "wyjątkami". Mogą one obejmować wyczerpanie pamięci, błędy alokacji zasobów i nieznalezienie plików.

Biblioteka klas Programu Microsoft Foundation używa schematu obsługi wyjątków, który jest ściśle modelowany po schemacie zaproponowanym przez komitet standardów ANSI dla języka C++. Program obsługi wyjątków musi być skonfigurowany przed wywołaniem funkcji, która może napotkać nienormalną sytuację. Jeśli funkcja napotka nieprawidłowy warunek, zgłasza wyjątek i kontroli jest przekazywana do obsługi wyjątków.

Kilka makr dołączonych do biblioteki klas programu Microsoft Foundation skonfiguruje programy obsługi wyjątków. Wiele innych funkcji globalnych pomaga zgłaszać wyjątki specjalistyczne i w razie potrzeby kończyć programy. Te makra i funkcje globalne dzielą się na następujące kategorie:

- Makra wyjątków, które struktury obsługi wyjątków.

- Funkcje zgłaszania wyjątków), które generują wyjątki określonych typów.

- Funkcje zakończenia, które powodują zakończenie programu.

Aby uzyskać przykłady i więcej szczegółów, zobacz artykuł [Wyjątki](../../mfc/exception-handling-in-mfc.md).

### <a name="exception-macros"></a>Makra wyjątków

|||
|-|-|
|[Spróbuj](#try)|Wyznacza blok kodu do przetwarzania wyjątków.|
|[Złapać](#catch)|Wyznacza blok kodu do przechwytywania wyjątek z poprzedniego **try** bloku.|
|[CATCH_ALL](#catch_all)|Wyznacza blok kodu do przechwytywania wszystkich wyjątków z poprzedniego bloku **TRY.**|
|[AND_CATCH](#and_catch)|Wyznacza blok kodu do przechwytywania dodatkowych typów wyjątków z poprzedniego bloku **TRY.**|
|[AND_CATCH_ALL](#and_catch_all)|Wyznacza blok kodu do przechwytywania wszystkich innych dodatkowych typów wyjątków zgłoszonych w poprzednim bloku **TRY.**|
|[END_CATCH](#end_catch)|Kończy ostatni blok kodu **CATCH** lub **AND_CATCH.**|
|[END_CATCH_ALL](#end_catch_all)|Kończy ostatni blok kodu **CATCH_ALL.**|
|[Rzucać](#throw)|Zgłasza określony wyjątek.|
|[THROW_LAST](#throw_last)|Zgłasza aktualnie obsługiwany wyjątek do następnego zewnętrznego programu obsługi.|

### <a name="exception-throwing-functions"></a>Funkcje zgłaszania wyjątków

|||
|-|-|
|[AfxThrowArchiveException (Nieeksceptacja afxthrowarchiveexception)](#afxthrowarchiveexception)|Zgłasza wyjątek archiwum.|
|[AfxThrowFileException (Nieekceptacja)](#afxthrowfileexception)|Zgłasza wyjątek pliku.|
|[AfxThrowInvalidArgWynik z wyjątkiem](#afxthrowinvalidargexception)|Zgłasza wyjątek nieprawidłowego argumentu.|
|[AfxThrowMemoryEkstawa](#afxthrowmemoryexception)|Zgłasza wyjątek pamięci.|
|[AfxThrowNotSupportedException (Niewsienie)](#afxthrownotsupportedexception)|Zgłasza nie obsługiwany wyjątek.|
|[AfxThrowResourceEkcepta](#afxthrowresourceexception)|Zgłasza wyjątek nieuleczany przez zasoby systemu Windows.|
|[AfxThrowUserException (Nieekceptacja)](#afxthrowuserexception)|Zgłasza wyjątek w akcji programu inicjowanej przez użytkownika.|

MFC udostępnia dwie funkcje zgłaszania wyjątków specjalnie dla wyjątków OLE:

### <a name="ole-exception-functions"></a>Funkcje wyjątków OLE

|||
|-|-|
|[AfxThrowOleDispatchWynik](#afxthrowoledispatchexception)|Zgłasza wyjątek w ramach funkcji automatyzacji OLE.|
|[AfxThrowOleException (Nieekceptycja afxthrowole)](#afxthrowoleexception)|Zgłasza wyjątek OLE.|

Aby obsługiwać wyjątki bazy danych, klasy `CDBException` `CDaoException`bazy danych zapewniają dwie klasy wyjątków i , i funkcje globalne do obsługi typów wyjątków:

### <a name="dao-exception-functions"></a>Funkcje wyjątków DAO

|||
|-|-|
|[AfxThrowDAOWynik](#afxthrowdaoexception)|Rzuca [CDaoException](../../mfc/reference/cdaoexception-class.md) z własnego kodu.|
|[AfxThrowDBException (Niedbywanie o afxthrowdb)](#afxthrowdbexception)|Rzuca [CDBException](../../mfc/reference/cdbexception-class.md) z własnego kodu.|

MFC zapewnia następującą funkcję zakończenia:

### <a name="termination-functions"></a>Funkcje zakończenia

|||
|-|-|
|[AfxAbort ( AfxAbort )](#afxabort)|Wywołany wobec kończyć an zgłoszenie podczas pewien krytyczny błąd wystąpi.|

## <a name="try"></a><a name="try"></a>Spróbuj

Konfiguruje blok **TRY.**

```
TRY
```

### <a name="remarks"></a>Uwagi

Blok **TRY** identyfikuje blok kodu, który może zgłaszać wyjątki. Wyjątki te są obsługiwane w następujących **catch** i **AND_CATCH** bloków. Rekursja jest dozwolona: wyjątki mogą być przekazywane do zewnętrznego bloku **TRY,** ignorując je lub używając makra THROW_LAST. Zakończ blok **TRY** END_CATCH lub END_CATCH_ALL makra.

Aby uzyskać więcej informacji, zobacz artykuł [Wyjątki](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Przykład

Zobacz przykład [dla CATCH](#catch).

### <a name="requirements"></a>Wymagania

Nagłówek: afx.h

## <a name="catch"></a><a name="catch"></a>Złapać

Definiuje blok kodu, który połowy pierwszy typ wyjątku zgłoszony w poprzednim bloku **TRY.**

```
CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_class*<br/>
Określa typ wyjątku, dla jaki ma być test. Aby uzyskać listę standardowych klas wyjątków, zobacz klasę [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Określa nazwę wskaźnika obiektu wyjątku, który zostanie utworzony przez makro. Można użyć nazwy wskaźnika, aby uzyskać dostęp do obiektu wyjątku w bloku **CATCH.** Ta zmienna jest zadeklarowana dla Ciebie.

### <a name="remarks"></a>Uwagi

Kod przetwarzania wyjątków można przesłuchiwać obiekt wyjątku, w razie potrzeby, aby uzyskać więcej informacji na temat określonej przyczyny wyjątku. Wywołaj makro THROW_LAST, aby przesunąć przetwarzanie do następnej zewnętrznej ramki wyjątku. Zakończ blok **TRY** END_CATCH makra.

Jeśli *exception_class* jest klasa `CException`, a następnie wszystkie typy wyjątków zostaną przechwycone. Można użyć [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof) funkcji elementu członkowskiego, aby określić, który wyjątek określony. Lepszym sposobem na złapanie kilku rodzajów wyjątków jest użycie sekwencyjnych **instrukcji AND_CATCH,** z których każdy ma inny typ wyjątku.

Wskaźnik obiektu wyjątku jest tworzony przez makro. Nie musisz tego deklarować samodzielnie.

> [!NOTE]
> Blok **CATCH** jest zdefiniowany jako zakres C++ nakreślony przez nawiasy klamrowe. Jeśli deklarujesz zmienne w tym zakresie, są one dostępne tylko w tym zakresie. Dotyczy to również *exception_object_pointer_name*.

Aby uzyskać więcej informacji na temat wyjątków i makra CATCH, zobacz artykuł [Wyjątki](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

## <a name="catch_all"></a><a name="catch_all"></a>CATCH_ALL

Definiuje blok kodu, który przechwytuje wszystkie typy wyjątków zgłaszane w poprzednim bloku **TRY.**

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_object_pointer_name*<br/>
Określa nazwę wskaźnika obiektu wyjątku, który zostanie utworzony przez makro. Za pomocą nazwy wskaźnika można uzyskać `CATCH_ALL` dostęp do obiektu wyjątku w bloku. Ta zmienna jest zadeklarowana dla Ciebie.

### <a name="remarks"></a>Uwagi

Kod przetwarzania wyjątków można przesłuchiwać obiekt wyjątku, w razie potrzeby, aby uzyskać więcej informacji na temat określonej przyczyny wyjątku. Wywołaj `THROW_LAST` makro, aby przesunąć przetwarzanie do następnej zewnętrznej ramki wyjątku. Jeśli używasz **CATCH_ALL,** zakończ blok **TRY** END_CATCH_ALL makrą.

> [!NOTE]
> Blok **CATCH_ALL** jest zdefiniowany jako zakres C++ nakreślony przez nawiasy klamrowe. Jeśli deklarujesz zmienne w tym zakresie, są one dostępne tylko w tym zakresie.

Aby uzyskać więcej informacji na temat wyjątków, zobacz artykuł [Wyjątki](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Przykład

Zobacz przykład [CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

## <a name="and_catch"></a><a name="and_catch"></a>AND_CATCH

Definiuje blok kodu do przechwytywania dodatkowych typów wyjątków zgłoszonych w poprzednim bloku **TRY.**

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_class*<br/>
Określa typ wyjątku, dla jaki ma być test. Aby uzyskać listę standardowych klas wyjątków, zobacz klasę [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Nazwa wskaźnika obiektu wyjątku, który zostanie utworzony przez makro. Za pomocą nazwy wskaźnika można uzyskać dostęp do obiektu wyjątku w bloku **AND_CATCH.** Ta zmienna jest zadeklarowana dla Ciebie.

### <a name="remarks"></a>Uwagi

Użyj makra CATCH, aby złapać jeden typ wyjątku, a następnie makro AND_CATCH, aby złapać każdy kolejny typ. Zakończ blok **TRY** END_CATCH makra.

Kod przetwarzania wyjątków można przesłuchiwać obiekt wyjątku, w razie potrzeby, aby uzyskać więcej informacji na temat określonej przyczyny wyjątku. Wywołanie makra THROW_LAST w bloku **AND_CATCH,** aby przenieść przetwarzanie do następnej zewnętrznej ramki wyjątku. **AND_CATCH** oznacza koniec poprzedniego **catch** lub **AND_CATCH** bloku.

> [!NOTE]
> Blok **AND_CATCH** jest zdefiniowany jako zakres C++ (nakreślony nawiasami klamrowymi). Jeśli deklarujesz zmienne w tym zakresie, należy pamiętać, że są one dostępne tylko w tym zakresie. Dotyczy to również zmiennej *exception_object_pointer_name.*

### <a name="example"></a>Przykład

Zobacz przykład [dla CATCH](#catch).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

## <a name="and_catch_all"></a><a name="and_catch_all"></a>AND_CATCH_ALL

Definiuje blok kodu do przechwytywania dodatkowych typów wyjątków zgłoszonych w poprzednim bloku **TRY.**

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_object_pointer_name*<br/>
Nazwa wskaźnika obiektu wyjątku, który zostanie utworzony przez makro. Za pomocą nazwy wskaźnika można uzyskać dostęp do obiektu wyjątku w bloku **AND_CATCH_ALL.** Ta zmienna jest zadeklarowana dla Ciebie.

### <a name="remarks"></a>Uwagi

Użyj makra **CATCH,** aby złapać jeden typ wyjątku, a następnie makro AND_CATCH_ALL, aby wychwyć wszystkie inne kolejne typy. Jeśli używasz AND_CATCH_ALL, zakończ blok **TRY** END_CATCH_ALL makra.

Kod przetwarzania wyjątków można przesłuchiwać obiekt wyjątku, w razie potrzeby, aby uzyskać więcej informacji na temat określonej przyczyny wyjątku. Wywołanie makra THROW_LAST w bloku **AND_CATCH_ALL,** aby przenieść przetwarzanie do następnej zewnętrznej ramki wyjątku. **AND_CATCH_ALL** oznacza koniec poprzedniego **catch** lub **AND_CATCH_ALL** bloku.

> [!NOTE]
> Blok **AND_CATCH_ALL** jest zdefiniowany jako zakres C++ (nakreślony przez nawiasy klamrowe). Jeśli deklarujesz zmienne w tym zakresie, należy pamiętać, że są one dostępne tylko w tym zakresie.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

## <a name="end_catch"></a><a name="end_catch"></a>END_CATCH

Oznacza koniec ostatniego **catch** lub **AND_CATCH** bloku.

```
END_CATCH
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat makra END_CATCH, zobacz artykuł [Wyjątki](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

## <a name="end_catch_all"></a><a name="end_catch_all"></a>END_CATCH_ALL

Oznacza koniec ostatniego **bloku CATCH_ALL88** lub **AND_CATCH_ALL.**

```
END_CATCH_ALL
```

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

## <a name="throw-mfc"></a><a name="throw"></a>RZUT (MFC)

Zgłasza określony wyjątek.

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>Parametry

*exception_object_pointer*<br/>
Wskazuje obiekt wyjątku uzyskany z `CException`programu .

### <a name="remarks"></a>Uwagi

**THROW** przerywa wykonywanie programu, przekazując kontrolę do skojarzonego bloku **CATCH** w programie. Jeśli nie podano **catch** bloku, a następnie formant jest przekazywany do modułu Biblioteki klas Microsoft Foundation, który drukuje komunikat o błędzie i kończy pracę.

Aby uzyskać więcej informacji, zobacz artykuł [Wyjątki](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

## <a name="throw_last"></a><a name="throw_last"></a>THROW_LAST

Zgłasza wyjątek z powrotem do następnego **zewnętrznego** catch bloku.

```
THROW_LAST()
```

### <a name="remarks"></a>Uwagi

To makro umożliwia zgłaszanie wyjątku utworzonego lokalnie. Jeśli spróbujesz zgłosić wyjątek, który właśnie został przechwycony, zwykle wykracza poza zakres i zostanie usunięty. Z **THROW_LAST**, wyjątek jest przekazywany poprawnie do następnego **catch** obsługi.

Aby uzyskać więcej informacji, zobacz artykuł [Wyjątki](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Przykład

Zobacz przykład [CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

## <a name="afxthrowarchiveexception"></a><a name="afxthrowarchiveexception"></a>AfxThrowArchiveException (Nieeksceptacja afxthrowarchiveexception)

Zgłasza wyjątek archiwum.

```cpp
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>Parametry

*Spowodować*<br/>
Określa liczbę całkowitą, która wskazuje przyczynę wyjątku. Aby uzyskać listę możliwych wartości, zobacz [CArchiveException::m_cause](../../mfc/reference/carchiveexception-class.md#m_cause).

*lpszArchiveName*<br/>
Wskazuje ciąg zawierający nazwę `CArchive` obiektu, który spowodował wyjątek (jeśli jest dostępny).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

## <a name="afxthrowfileexception"></a><a name="afxthrowfileexception"></a>AfxThrowFileException (Nieekceptacja)

Zgłasza wyjątek pliku.

```cpp
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parametry

*Spowodować*<br/>
Określa liczbę całkowitą, która wskazuje przyczynę wyjątku. Aby uzyskać listę możliwych wartości, zobacz [CFileException::m_cause](../../mfc/reference/cfileexception-class.md#m_cause).

*lOsError*<br/>
Zawiera numer błędu systemu operacyjnego (jeśli jest dostępny), który określa przyczynę wyjątku. Lista kodów błędów można znaleźć w instrukcji obsługi systemu operacyjnego.

*lpszFileName*<br/>
Wskazuje ciąg zawierający nazwę pliku, który spowodował wyjątek (jeśli jest dostępny).

### <a name="remarks"></a>Uwagi

Użytkownik jest odpowiedzialny za określenie przyczyny na podstawie kodu błędu systemu operacyjnego.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

## <a name="afxthrowinvalidargexception"></a><a name="afxthrowinvalidargexception"></a>AfxThrowInvalidArgWynik z wyjątkiem

Zgłasza wyjątek nieprawidłowego argumentu.

### <a name="syntax"></a>Składnia

```cpp
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana, gdy używane są nieprawidłowe argumenty.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="afxthrowmemoryexception"></a><a name="afxthrowmemoryexception"></a>AfxThrowMemoryEkstawa

Zgłasza wyjątek pamięci.

```cpp
void AfxThrowMemoryException();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, jeśli wywołania podstawowych alokatorów pamięci systemowej (takich jak **malloc** i [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) Windows, funkcja) nie powiedzie się. Nie trzeba wywoływać go dla **nowych,** ponieważ **nowy** zda wyjątek pamięci automatycznie, jeśli alokacja pamięci nie powiedzie się.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

## <a name="afxthrownotsupportedexception"></a><a name="afxthrownotsupportedexception"></a>AfxThrowNotSupportedException (Niewsienie)

Zgłasza wyjątek, który jest wynikiem żądania dla nieobsługiconej funkcji.

```cpp
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

## <a name="afxthrowresourceexception"></a><a name="afxthrowresourceexception"></a>AfxThrowResourceEkcepta

Zgłasza wyjątek zasobu.

```cpp
void  AfxThrowResourceException();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest zwykle wywoływana, gdy nie można załadować zasobu systemu Windows.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

## <a name="afxthrowuserexception"></a><a name="afxthrowuserexception"></a>AfxThrowUserException (Nieekceptacja)

Zgłasza wyjątek, aby zatrzymać operację użytkownika końcowego.

```cpp
void AfxThrowUserException();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest zwykle `AfxMessageBox` wywoływana natychmiast po zgłoszeniu błędu do użytkownika.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

## <a name="afxthrowoledispatchexception"></a><a name="afxthrowoledispatchexception"></a>AfxThrowOleDispatchWynik

Ta funkcja służy do zgłaszania wyjątku w ramach funkcji automatyzacji OLE.

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

*wKod*<br/>
Kod błędu specyficzny dla aplikacji.

*lpszDescription*<br/>
Słowny opis błędu.

*nDescriptionID*<br/>
Identyfikator zasobu dla opisu błędu werbalnego.

*nHelpID (Pomoc eksmisja)*<br/>
Kontekst pomocy dla pomocy aplikacji (. HLP).

### <a name="remarks"></a>Uwagi

Informacje podane do tej funkcji mogą być wyświetlane przez aplikację driving (Microsoft Visual Basic lub inną aplikację kliencką automatyzacji OLE).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

## <a name="afxthrowoleexception"></a><a name="afxthrowoleexception"></a>AfxThrowOleException (Nieekceptycja afxthrowole)

Tworzy obiekt typu `COleException` i zgłasza wyjątek.

```cpp
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>Parametry

*Sc*<br/>
Kod stanu OLE, który wskazuje przyczynę wyjątku.

*Hr*<br/>
Dojmij do kodu wynikowego, który wskazuje przyczynę wyjątku.

### <a name="remarks"></a>Uwagi

Wersja, która przyjmuje HRESULT jako argument konwertuje ten kod wyniku do odpowiedniego SCODE. Aby uzyskać więcej informacji na temat HRESULT i SCODE, zobacz [Struktura kodów błędów COM](/windows/win32/com/structure-of-com-error-codes) w windows SDK.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

## <a name="afxthrowdaoexception"></a><a name="afxthrowdaoexception"></a>AfxThrowDaoWynik

Wywołanie tej funkcji, aby zgłosić wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md) z własnego kodu.

```cpp
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>Parametry

*nAfxDaoError*<br/>
Wartość całkowita reprezentująca rozszerzony kod błędu DAO, który może być jedną z wartości wymienionych w obszarze [CDaoException::m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror).

*Scode*<br/>
Kod błędu OLE z DAO typu SCODE. Aby uzyskać więcej informacji, zobacz [CDaoException::m_scode](../../mfc/reference/cdaoexception-class.md#m_scode).

### <a name="remarks"></a>Uwagi

Ramy te `AfxThrowDaoException`również wzywają . W połączeniu można przekazać jeden z parametrów lub oba. Na przykład, jeśli chcesz podnieść jeden z błędów zdefiniowanych w **CDaoException::nAfxDaoError,** ale nie dbasz o parametr *scode,* przekaż prawidłowy kod w parametrze *nAfxDaoError* i zaakceptuj domyślną wartość *scode*.

Aby uzyskać informacje na temat wyjątków związanych `CDaoException` z klasami DAO MFC, zobacz klasę w tej książce i artykuł [Wyjątki: Wyjątki bazy danych](../../mfc/exceptions-database-exceptions.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdb.h

## <a name="afxthrowdbexception"></a><a name="afxthrowdbexception"></a>AfxThrowDBException (Niedbywanie o afxthrowdb)

Wywołanie tej funkcji, aby `CDBException` zgłosić wyjątek typu z własnego kodu.

```cpp
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*kod nRetCode*<br/>
Wartość typu RETCODE, definiując typ błędu, który spowodował wyjątek.

*Pdb*<br/>
Wskaźnik do `CDatabase` obiektu, który reprezentuje połączenie źródła danych, z którym jest skojarzony wyjątek.

*Hstmt*<br/>
Dojście HSTMT ODBC, który określa dojście instrukcji, z którym jest skojarzony wyjątek.

### <a name="remarks"></a>Uwagi

Struktura wywołuje, `AfxThrowDBException` gdy odbiera ODBC RETCODE z wywołania funkcji interfejsu API ODBC i interpretuje RETCODE jako warunek wyjątkowy, a nie oczekiwany błąd. Na przykład operacja dostępu do danych może zakończyć się niepowodzeniem z powodu błędu odczytu dysku.

Aby uzyskać informacje na temat wartości RETCODE zdefiniowanych przez ODBC, zobacz rozdział 8, "Pobieranie informacji o stanie i błędzie" w sdk systemu Windows. Aby uzyskać informacje na temat rozszerzeń MFC do tych kodów, zobacz klasa [CDBException](../../mfc/reference/cdbexception-class.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

## <a name="afxabort"></a><a name="afxabort"></a>AfxAbort ( AfxAbort )

Domyślna funkcja zakończenia dostarczona przez MFC.

```cpp
void  AfxAbort();
```

### <a name="remarks"></a>Uwagi

`AfxAbort`jest wywoływana wewnętrznie przez funkcje członkowskie MFC, gdy występuje błąd krytyczny, takich jak nieprzechowywanego wyjątku, który nie może być obsługiwany. Można wywołać `AfxAbort` w rzadkich przypadkach, gdy wystąpi katastrofalny błąd, z którego nie można odzyskać.

### <a name="example"></a>Przykład

Zobacz przykład [dla CATCH](#catch).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afx.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](mfc-macros-and-globals.md)<br/>
[Klasa CException](cexception-class.md)<br/>
[Klasa CInvalidArgException](cinvalidargexception-class.md)
