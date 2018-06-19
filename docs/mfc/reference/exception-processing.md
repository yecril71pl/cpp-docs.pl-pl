---
title: Wyjątek podczas przetwarzania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.exceptions
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a24d78089e468a2020e0ecdb1fba34783965325
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376991"
---
# <a name="exception-processing"></a>Przetwarzanie wyjątków
Podczas program, może wystąpić wiele anomalii i błędy o nazwie "wyjątki". Mogą one obejmować brakiem pamięci, błędy alokacji zasobów i nie można odnaleźć plików.  
  
 Microsoft Foundation Class Library używa schematu obsługi wyjątków jest modelowane dokładnie jedną proponowane Komitet standardy ANSI dla języka C++. Przed wywołanie funkcji, które mogą wystąpić sytuacja nietypowe można skonfigurować program obsługi wyjątku. Jeśli funkcja napotkał nieprawidłowy warunek, zgłasza wyjątek i kontrola jest przekazywana do obsługi wyjątków.  
  
 Makra kilka dołączonego Microsoft Foundation Class Library skonfiguruje programy obsługi wyjątków. Liczba innych funkcje globalne pomóc zgłaszają wyjątki specjalne i zakończyć programy, w razie potrzeby. Te makra i funkcje globalne można podzielić na następujące kategorie:  
  
- Makra wyjątków, które struktury programu obsługi wyjątków.  
  
- Funkcje Exception-throwing), które generują wyjątki określonych typów.  
  
- Funkcje zakończenia, które powodują Kończenie działania programu.  
  
 Aby uzyskać bardziej szczegółowe informacje i przykłady, zobacz artykuł [wyjątki](../../mfc/exception-handling-in-mfc.md).  
  
### <a name="exception-macros"></a>Makra wyjątków  
  
|||  
|-|-|  
|[SPRÓBUJ](#try)|Określa blok kodu dla wyjątek podczas przetwarzania.|  
|[CATCH](#catch)|Określa blok kodu dla przechwytywanie wyjątku z poprzednim **SPRÓBUJ** bloku.|  
|[CATCH_ALL —](#catch_all)|Określa blok kodu dla Przechwytywanie wszystkich wyjątków z poprzednim **SPRÓBUJ** bloku.|  
|[AND_CATCH —](#and_catch)|Określa blok kodu dla Przechwytywanie typów wyjątków dodatkowych z poprzednim **SPRÓBUJ** bloku.|  
|[AND_CATCH_ALL —](#and_catch_all)|Określa blok kodu dla wszystkich pozostałych typów dodatkowe wyjątek zgłoszony w poprzednich Przechwytywanie **SPRÓBUJ** bloku.|  
|[END_CATCH —](#end_catch)|Kończy się ostatniego **CATCH** lub `AND_CATCH` blok kodu.|  
|[END_CATCH_ALL —](#end_catch_all)|Kończy się ostatniego `CATCH_ALL` blok kodu.|  
|[THROW](#throw)|Zwraca określony wyjątek.|  
|[THROW_LAST —](#throw_last)|Zwraca aktualnie obsługiwany wyjątku, aby dalej zewnętrzny program obsługi.|  
  
### <a name="exception-throwing-functions"></a>Funkcje Wyrzucające wyjątki  
  
|||  
|-|-|  
|[Afxthrowarchiveexception —](#afxthrowarchiveexception)|Zgłasza wyjątek archiwum.|  
|[Afxthrowfileexception —](#afxthrowfileexception)|Zgłasza wyjątek plików.|  
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|Zgłasza wyjątek nieprawidłowego argumentu.|
|[Afxthrowmemoryexception —](#afxthrowmemoryexception)|Zgłasza wyjątek pamięci.|  
|[Afxthrownotsupportedexception —](#afxthrownotsupportedexception)|Zgłasza wyjątek nie obsługiwane.|  
|[Afxthrowresourceexception —](#afxthrowresourceexception)|Zgłasza wyjątek zasobu nie można odnaleźć systemu Windows.|  
|[Afxthrowuserexception —](#afxthrowuserexception)|Zgłasza wyjątek w działaniu programu zainicjowanego przez użytkownika.|  
  
 MFC oferuje dwie funkcje wyrzucające wyjątki specjalnie z myślą o wyjątki OLE:  
  
### <a name="ole-exception-functions"></a>Funkcje wyjątek OLE  
  
|||  
|-|-|  
|[Afxthrowoledispatchexception —](#afxthrowoledispatchexception)|Zgłasza wyjątek w funkcji automatyzacji OLE.|  
|[Afxthrowoleexception —](#afxthrowoleexception)|Zgłasza wyjątek OLE.|  
  
 Aby zapewnić obsługę wyjątków bazy danych, klas baz danych Podaj dwie klasy wyjątków, `CDBException` i `CDaoException`i funkcje globalne do obsługi typów wyjątków:  
  
### <a name="dao-exception-functions"></a>Funkcje wyjątek DAO  
  
|||  
|-|-|  
|[Afxthrowdaoexception —](#afxthrowdaoexception)|Zgłasza wyjątek [CDaoException](../../mfc/reference/cdaoexception-class.md) z własnego kodu.|  
|[Afxthrowdbexception —](#afxthrowdbexception)|Zgłasza wyjątek [CDBException](../../mfc/reference/cdbexception-class.md) z własnego kodu.|  
  
 MFC udostępnia funkcję następujące rozwiązania:  
  
### <a name="termination-functions"></a>Funkcje zakończenia  
  
|||  
|-|-|  
|[Afxabort —](#afxabort)|Wywołuje się, aby zakończyć aplikację, jeśli błąd krytyczny występuje.|  
  
##  <a name="try"></a>  SPRÓBUJ  
 Konfiguruje **SPRÓBUJ** bloku.  
  
```   
TRY   
```  
  
### <a name="remarks"></a>Uwagi  
 A **SPRÓBUJ** bloku identyfikuje blok kodu, który może zgłaszać wyjątków. Te wyjątki są obsługiwane w następujących **CATCH** i `AND_CATCH` bloków. Rekursja jest dozwolona: wyjątki mogą zostać przekazane do zewnętrznego **SPRÓBUJ** bloku, pomijając je lub za pomocą `THROW_LAST` makra. Końcowy **SPRÓBUJ** zablokować z `END_CATCH` lub `END_CATCH_ALL` makra.  
  
 Aby uzyskać więcej informacji, zobacz artykuł [wyjątki](../../mfc/exception-handling-in-mfc.md).  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CATCH](#catch).  

### <a name="requirements"></a>Wymagania
Nagłówek: afx.h

##  <a name="catch"></a>  CATCH  
 Określa blok kodu, który przechwytuje pierwszego typu wyjątek zgłoszony w poprzednim **SPRÓBUJ** bloku.  
  
```   
CATCH(exception_class, exception_object_pointer_name)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *exception_class*  
 Określa typ wyjątku do testowania. Lista klas standardowe wyjątków, zobacz klasy [cexception —](../../mfc/reference/cexception-class.md).  
  
 *exception_object_pointer_name*  
 Określa nazwę dla obiekt wyjątku wskaźnika, który zostanie utworzony przez makro. Nazwa wskaźnika umożliwia dostęp do obiektu wyjątek w **CATCH** bloku. Ta zmienna jest zadeklarowana dla Ciebie.  
  
### <a name="remarks"></a>Uwagi  
 Kod wyjątku przetwarzania można przejrzeć obiekt wyjątku, w razie potrzeby uzyskać więcej informacji na temat określonego powodu wyjątku. Wywołanie `THROW_LAST` makra, które mają zostać przesunięte przetwarzania do następnej ramki Wyjątek zewnętrzny. Końcowy **SPRÓBUJ** zablokować z `END_CATCH` makra.  
  
 Jeśli *exception_class* jest klasa `CException`, a następnie wszystkie typy wyjątek zostanie przechwycony. Można użyć [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof) funkcji członkowskiej, aby określić, które określony wyjątek został zgłoszony. Lepszym sposobem catch kilka rodzajów wyjątków jest użycie sekwencyjnych `AND_CATCH` instrukcje, każda z innego typu wyjątku.  
  
 Wskaźnik do obiektu wyjątku jest tworzony przez makro. Nie trzeba zadeklarować samodzielnie.  
  
> [!NOTE]
>  **CATCH** bloku jest zdefiniowany jako zakres C++ ograniczona przez nawiasów klamrowych. Deklarowanie zmiennych w tym zakresie, są one dostępne tylko w ramach tego zakresu. Dotyczy to również *exception_object_pointer_name*.  
  
 Aby uzyskać więcej informacji na temat wyjątków i **CATCH** makra, zapoznaj się z artykułem [wyjątki](../../mfc/exception-handling-in-mfc.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]  
  
##  <a name="catch_all"></a>  CATCH_ALL —  
 Określa blok kodu, który przechwytuje wszystkie typy wyjątków zgłoszonych w poprzednim **SPRÓBUJ** bloku.  
  
```   
CATCH_ALL(exception_object_pointer_name)   
```  
  
### <a name="parameters"></a>Parametry  
 *exception_object_pointer_name*  
 Określa nazwę dla obiekt wyjątku wskaźnika, który zostanie utworzony przez makro. Nazwa wskaźnika umożliwia dostęp do obiektu wyjątek w `CATCH_ALL` bloku. Ta zmienna jest zadeklarowana dla Ciebie.  
  
### <a name="remarks"></a>Uwagi  
 Kod wyjątku przetwarzania można przejrzeć obiekt wyjątku, w razie potrzeby uzyskać więcej informacji na temat określonego powodu wyjątku. Wywołanie `THROW_LAST` makra, które mają zostać przesunięte przetwarzania do następnej ramki Wyjątek zewnętrzny. Jeśli używasz `CATCH_ALL`, koniec **SPRÓBUJ** zablokować z `END_CATCH_ALL` makra.  
  
> [!NOTE]
>  `CATCH_ALL` Bloku jest zdefiniowany jako zakres C++ ograniczona przez nawiasów klamrowych. Deklarowanie zmiennych w tym zakresie, są one dostępne tylko w ramach tego zakresu.  
  
 Aby uzyskać więcej informacji na wyjątki, zobacz artykuł [wyjątki](../../mfc/exception-handling-in-mfc.md).  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CFile::Abort](../../mfc/reference/cfile-class.md#abort).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afx.h  

##  <a name="and_catch"></a>  AND_CATCH —  
 Określa blok kodu dla Przechwytywanie typów wyjątków dodatkowe zgłoszony w poprzednich **SPRÓBUJ** bloku.  
  
```   
AND_CATCH(exception_class, exception_object_pointer_name)   
```  
  
### <a name="parameters"></a>Parametry  
 *exception_class*  
 Określa typ wyjątku do testowania. Lista klas standardowe wyjątków, zobacz klasy [cexception —](../../mfc/reference/cexception-class.md).  
  
 *exception_object_pointer_name*  
 Nazwa wskaźnika obiekt wyjątku, który zostanie utworzony przez makro. Nazwa wskaźnika umożliwia dostęp do obiektu wyjątek w `AND_CATCH` bloku. Ta zmienna jest zadeklarowana dla Ciebie.  
  
### <a name="remarks"></a>Uwagi  
 Użyj **CATCH** makro catch jeden typ wyjątku, a następnie `AND_CATCH` makra, aby przechwycić każdego typu kolejne. Końcowy **SPRÓBUJ** zablokować z `END_CATCH` makra.  
  
 Kod wyjątku przetwarzania można przejrzeć obiekt wyjątku, w razie potrzeby uzyskać więcej informacji na temat określonego powodu wyjątku. Wywołanie `THROW_LAST` makra w `AND_CATCH` shift przetwarzania do następnej ramki Wyjątek zewnętrzny za pomocą bloku. `AND_CATCH` oznacza koniec poprzedniego **CATCH** lub `AND_CATCH` bloku.  
  
> [!NOTE]
>  `AND_CATCH` Blok jest zdefiniowany jako zakres C++ (ograniczona przez nawiasy klamrowe). Deklarowanie zmiennych w tym zakresie, należy pamiętać, że są one dostępne tylko w ramach tego zakresu. Dotyczy to również *exception_object_pointer_name* zmiennej.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CATCH](#catch).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afx.h  
##  <a name="and_catch_all"></a>  AND_CATCH_ALL —  
 Określa blok kodu dla Przechwytywanie typów wyjątków dodatkowe zgłoszony w poprzednich **SPRÓBUJ** bloku.  
  
```   
AND_CATCH_ALL(exception_object_pointer_name)  
```  
  
### <a name="parameters"></a>Parametry  
 *exception_object_pointer_name*  
 Nazwa wskaźnika obiekt wyjątku, który zostanie utworzony przez makro. Nazwa wskaźnika umożliwia dostęp do obiektu wyjątek w `AND_CATCH_ALL` bloku. Ta zmienna jest zadeklarowana dla Ciebie.  
  
### <a name="remarks"></a>Uwagi  
 Użyj **CATCH** makro catch jeden typ wyjątku, a następnie `AND_CATCH_ALL` makra, aby przechwycić wszystkie inne kolejne typy. Jeśli używasz `AND_CATCH_ALL`, koniec **SPRÓBUJ** zablokować z `END_CATCH_ALL` makra.  
  
 Kod wyjątku przetwarzania można przejrzeć obiekt wyjątku, w razie potrzeby uzyskać więcej informacji na temat określonego powodu wyjątku. Wywołanie `THROW_LAST` makra w `AND_CATCH_ALL` shift przetwarzania do następnej ramki Wyjątek zewnętrzny za pomocą bloku. `AND_CATCH_ALL` oznacza koniec poprzedniego **CATCH** lub `AND_CATCH_ALL` bloku.  
  
> [!NOTE]
>  `AND_CATCH_ALL` Bloku jest zdefiniowany jako zakres C++ (ograniczona klamrowym). Deklarowanie zmiennych w tym zakresie, należy pamiętać, że są one dostępne tylko w ramach tego zakresu.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afx.h  
  
##  <a name="end_catch"></a>  END_CATCH —  
 Oznacza koniec ostatniego **CATCH** lub `AND_CATCH` bloku.  
  
```   
END_CATCH  
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat `END_CATCH` makra, zapoznaj się z artykułem [wyjątki](../../mfc/exception-handling-in-mfc.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afx.h  
  
##  <a name="end_catch_all"></a>  END_CATCH_ALL —  
 Oznacza koniec ostatniego `CATCH_ALL` lub `AND_CATCH_ALL` bloku.  
  
```   
END_CATCH_ALL  
```  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afx.h  
  
##  <a name="throw"></a>  THROW (MFC)  
 Zwraca określony wyjątek.  
  
```   
THROW(exception_object_pointer) 
```  
  
### <a name="parameters"></a>Parametry  
 *exception_object_pointer*  
 Wskazuje obiekt wyjątku pochodzących z `CException`.  
  
### <a name="remarks"></a>Uwagi  
 **THROW** wykonywania przekazanie sterowania do skojarzonego programu przerwań **CATCH** Blokuj w programie. Jeśli nie podano **CATCH** zablokować, a następnie kontrola jest przekazywana do modułu Microsoft Foundation Class Library, która odbitek błąd wiadomości i kończy działanie.  
  
 Aby uzyskać więcej informacji, zobacz artykuł [wyjątki](../../mfc/exception-handling-in-mfc.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afx.h  
  
##  <a name="throw_last"></a>  THROW_LAST —  
 Zgłasza wyjątek z powrotem do następnego zewnętrzne **CATCH** bloku.  
  
```   
THROW_LAST()   
```  
  
### <a name="remarks"></a>Uwagi  
 To makro umożliwia zgłoszenie wyjątku utworzony lokalnie. Jeśli spróbujesz zgłosić wyjątek, który ma właśnie przechwycono zazwyczaj będzie się znaleźć poza zakresem i go usunąć. Z `THROW_LAST`, wyjątek jest prawidłowo przekazane do następnego **CATCH** obsługi.  
  
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
 `cause`  
 Określa liczbę całkowitą, która wskazuje przyczynę wyjątek. Aby uzyskać listę możliwych wartości, zobacz [CArchiveException::m_cause](../../mfc/reference/carchiveexception-class.md#m_cause).  
  
 `lpszArchiveName`  
 Wskazuje ciąg zawierający nazwę `CArchive` obiektu, który spowodował wyjątek (jeśli jest dostępna).  
  
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
 `cause`  
 Określa liczbę całkowitą, która wskazuje przyczynę wyjątek. Aby uzyskać listę możliwych wartości, zobacz [CFileException::m_cause](../../mfc/reference/cfileexception-class.md#m_cause).  
  
 `lOsError`  
 Zawiera kod błędu systemu operacyjnego (jeśli jest dostępny) który powód wyjątek. Znaleźć w podręczniku użytkownika systemu operacyjnego, aby uzyskać listę kodów błędów.  
  
 `lpszFileName`  
 Wskazuje ciąg zawierający nazwę pliku, który spowodował wyjątek (jeśli jest dostępna).  
  
### <a name="remarks"></a>Uwagi  
 Jest odpowiedzialny za ustalania przyczyny oparte na kod błędu systemu operacyjnego.  
  
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
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
 [Klasa CInvalidArgException](cinvalidargexception-class.md)   
 [THROW](#throw)
  
  
##  <a name="afxthrowmemoryexception"></a>  Afxthrowmemoryexception —  
 Zgłasza wyjątek pamięci.  
  
```   
void AfxThrowMemoryException(); 
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, jeśli wywołań podstawowej allocators — pamięci systemu (takich jak `malloc` i [działanie funkcji GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) funkcji systemu Windows) się nie powieść. Nie należy wywołać go w celu **nowe** ponieważ **nowe** zgłosi wyjątek pamięci automatycznie Jeśli alokacja pamięci nie powiedzie się.  
  
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
 Zgłasza wyjątek zasobów.  
  
```   
void  AfxThrowResourceException(); 
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana zwykle, gdy nie można załadować zasobów systemu Windows.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afx.h  
  
##  <a name="afxthrowuserexception"></a>  Afxthrowuserexception —  
 Zgłasza wyjątek, aby zatrzymać operację użytkownika końcowego.  
  
```   
void AfxThrowUserException(); 
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest zazwyczaj wywoływana natychmiast po `AfxMessageBox` zgłosił błąd dla użytkownika.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afx.h  
  
##  <a name="afxthrowoledispatchexception"></a>  Afxthrowoledispatchexception —  
 Ta funkcja służy do zgłoszenia wyjątku w funkcji automatyzacji OLE.  
  
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
 `wCode`  
 Błąd o kodzie specyficzne dla aplikacji.  
  
 `lpszDescription`  
 Ustne opis błędu.  
  
 `nDescriptionID`  
 Identyfikator zasobu opis ustne błędu.  
  
 `nHelpID`  
 Kontekst Pomoc Aby uzyskać pomoc w aplikacji (. Plik HLP).  
  
### <a name="remarks"></a>Uwagi  
 Informacje podane w tej funkcji mogą być wyświetlane przez aplikację pobudzenie (Microsoft Visual Basic lub innej aplikacji automatyzacji OLE).  
  
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
 `sc`  
 Kod stanu OLE wskazujący przyczynę wyjątek.  
  
 `hr`  
 Dojście do kod wyniku, który wskazuje przyczynę wyjątek.  
  
### <a name="remarks"></a>Uwagi  
 Wersji, która przyjmuje `HRESULT` jako argument konwertuje kod wyniku odpowiadającego `SCODE`. Aby uzyskać więcej informacji na temat `HRESULT` i `SCODE`, zobacz [struktury COM kody błędów](http://msdn.microsoft.com/library/windows/desktop/ms690088) w zestawie Windows SDK.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdao.h  
  
##  <a name="afxthrowdaoexception"></a>  Afxthrowdaoexception —  
 Wywołanie tej funkcji, aby zgłosić wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md) z własnego kodu.  
  
```   
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,  
    SCODE scode = S_OK); 
```  
  
### <a name="parameters"></a>Parametry  
 `nAfxDaoError`  
 Wartość całkowitą reprezentującą DAO, rozszerzony kod błędu, który może być jedna z wartości wymieniona w obszarze [CDaoException::m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror).  
  
 *scode*  
 Kod błędu OLE z DAO typu `SCODE`. Aby uzyskać informacje, zobacz [CDaoException::m_scode](../../mfc/reference/cdaoexception-class.md#m_scode).  
  
### <a name="remarks"></a>Uwagi  
 Struktura również wywołuje `AfxThrowDaoException`. W przypadku połączenia można przekazać jeden z parametrów lub oba. Na przykład, jeśli chcesz podnieść jedną z błędy są zdefiniowane w **CDaoException::nAfxDaoError** , ale nie zależy Ci *scode* parametru, Przekaż prawidłowy kod w `nAfxDaoError` parametru i zaakceptuj Wartość domyślna *scode*.  
  
 Informacje związane z klas MFC DAO wyjątków, zobacz klasy `CDaoException` w książce i artykułu [wyjątki: wyjątki bazy danych](../../mfc/exceptions-database-exceptions.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdb.h  
  
##  <a name="afxthrowdbexception"></a>  Afxthrowdbexception —  
 Wywołanie tej funkcji, aby zgłosić wyjątek typu `CDBException` z własnego kodu.  
  
```  
void AfxThrowDBException(
    RETCODE nRetCode,  
    CDatabase* pdb,  
    HSTMT hstmt);  
```  
  
### <a name="parameters"></a>Parametry  
 `nRetCode`  
 Wartości typu **RETCODE**, definiujący typ błędu, który spowodował wyjątek zostanie wygenerowany.  
  
 `pdb`  
 Wskaźnik do `CDatabase` obiekt, który reprezentuje połączenia źródła danych, z którym skojarzony jest wyjątek.  
  
 `hstmt`  
 ODBC **HSTMT** dojście określający dojście instrukcji, z którym skojarzony jest wyjątek.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania framework `AfxThrowDBException` po otrzymaniu ODBC **RETCODE** po wywołaniu interfejsu API ODBC działać i będą interpretowane przez **RETCODE** jako warunek wyjątkowych zamiast expectable błąd. Na przykład operacja dostępu do danych może zakończyć się niepowodzeniem z powodu błędu odczytu z dysku.  
  
 Aby uzyskać informacje o **RETCODE** wartości zdefiniowanych przez ODBC, zobacz rozdział 8, "Pobieranie stanu oraz informacje o błędzie," w zestawie Windows SDK. Zawiera informacje na temat rozszerzeń MFC do tych kodów, klasa [CDBException](../../mfc/reference/cdbexception-class.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afx.h  
  
##  <a name="afxabort"></a>  Afxabort —  
 Zakończenie domyślnej funkcji dostarczonych przez MFC.  
  
```   
void  AfxAbort(); 
```  
  
### <a name="remarks"></a>Uwagi  
 `AfxAbort` jest wywoływana wewnętrznie przez funkcje Członkowskie MFC po błąd krytyczny, takich jak nieprzechwycony wyjątek nie mogą być obsługiwane. Możesz wywołać `AfxAbort` w rzadkich przypadkach, gdy wystąpi błąd krytyczny, z którego nie można odzyskać.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CATCH](#catch).  

### <a name="requirements"></a>Wymagania  
  **Nagłówek** afx.h   
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)   
 [Klasa CException](../../mfc/reference/cexception-class.md)
