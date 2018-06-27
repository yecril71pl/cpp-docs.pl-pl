---
title: Klasa CFileException | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFileException
- AFX/CFileException
- AFX/CFileException::CFileException
- AFX/CFileException::ErrnoToException
- AFX/CFileException::GetErrorMessage
- AFX/CFileException::OsErrorToException
- AFX/CFileException::ThrowErrno
- AFX/CFileException::ThrowOsError
- AFX/CFileException::m_cause
- AFX/CFileException::m_lOsError
- AFX/CFileException::m_strFileName
dev_langs:
- C++
helpviewer_keywords:
- CFileException [MFC], CFileException
- CFileException [MFC], ErrnoToException
- CFileException [MFC], GetErrorMessage
- CFileException [MFC], OsErrorToException
- CFileException [MFC], ThrowErrno
- CFileException [MFC], ThrowOsError
- CFileException [MFC], m_cause
- CFileException [MFC], m_lOsError
- CFileException [MFC], m_strFileName
ms.assetid: f6491bb9-bfbc-42fd-a952-b33f9b62323f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df79b186aa515bba8d54083ad8a379aad36d2576
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954536"
---
# <a name="cfileexception-class"></a>Klasa CFileException
Reprezentuje stan wyjątek związany z plikami.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CFileException : public CException  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFileException::CFileException](#cfileexception)|Konstruuje `CFileException` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFileException::ErrnoToException](#errnotoexception)|Zwraca spowodować kod odpowiadający liczbą błędów czasu wykonywania.|  
|[CFileException::GetErrorMessage](#geterrormessage)|Pobiera komunikat opisujący wyjątek.|  
|[CFileException::OsErrorToException](#oserrortoexception)|Zwraca kod Przyczyna odpowiadający kod błędu systemu operacyjnego.|  
|[CFileException::ThrowErrno](#throwerrno)|Zgłasza wyjątek plików na podstawie różnych błąd czasu wykonywania.|  
|[CFileException::ThrowOsError](#throwoserror)|Zgłasza wyjątek plików na podstawie numeru błędu systemu operacyjnego.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFileException::m_cause](#m_cause)|Zawiera kod przenośny odpowiadający Przyczyna wyjątku.|  
|[CFileException::m_lOsError](#m_loserror)|Zawiera kod błędu systemu operacyjnego pokrewne.|  
|[CFileException::m_strFileName](#m_strfilename)|Zawiera nazwę pliku dla tego wyjątku.|  
  
## <a name="remarks"></a>Uwagi  
 `CFileException` Klasa zawiera publicznych elementów członkowskich danych zawierających kod przenośny Przyczyna i numer błędu operacyjnego specyficzne dla systemu. Klasa także statycznych funkcji Członkowskich zgłaszanie wyjątków pliku i zwracanie kodów Przyczyna zarówno błędy systemu operacyjnego i C błędów czasu wykonywania.  
  
 `CFileException` obiekty są konstruowane i zgłaszane w `CFile` funkcji Członkowskich oraz w funkcjach Członkowskich klas pochodnych. Można uzyskać dostępu do tych obiektów w zakresie **CATCH** wyrażenia. Przenośności Użyj tylko kod przyczyny, aby pobrać z powodu wyjątku. Aby uzyskać więcej informacji o wyjątkach, zobacz artykuł [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cexception —](../../mfc/reference/cexception-class.md)  
  
 `CFileException`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
  
##  <a name="cfileexception"></a>  CFileException::CFileException  
 Konstruuje `CFileException` obiekt zawierający kod Przyczyna i kod systemu operacyjnego w obiekcie.  
  
```  
CFileException(
    int cause = CFileException::none,  
    LONG lOsError = -1,  
    LPCTSTR lpszArchiveName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *Przyczyna*  
 Zmienna Typ wyliczany wskazujący przyczynę wyjątek. Zobacz [CFileException::m_cause](#m_cause) listę możliwych wartości.  
  
 *lOsError*  
 Działania — specyficzne dla systemu Przyczyna wyjątek, jeśli jest dostępna. *LOsError* parametru zapewnia więcej informacji niż *spowodować* jest.  
  
 *lpszArchiveName*  
 Wskazuje ciąg zawierający nazwę `CFile` obiektu wyjątku.  
  
### <a name="remarks"></a>Uwagi  
 Nie używaj tego konstruktora bezpośrednio, ale raczej wywołanie funkcji globalnych [afxthrowfileexception —](exception-processing.md#afxthrowfileexception).  
  
> [!NOTE]
>  Zmienna *lOsError* dotyczą tylko `CFile` i `CStdioFile` obiektów. `CMemFile` Klasa nie obsługuje tego kodu błędu.  
  
##  <a name="errnotoexception"></a>  CFileException::ErrnoToException  
 Konwertuje wartość błędu danej biblioteki wykonawczej `CFileException` wyliczyć wartość błędu.  
  
```  
static int PASCAL ErrnoToException(int nErrno);
```  
  
### <a name="parameters"></a>Parametry  
 *nErrno*  
 Kod błędu całkowitą zgodnie z definicją w pliku dołączanego środowiska wykonawczego numer błędu. H.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość wyliczeniowa odpowiada wartości błąd danej biblioteki czasu wykonywania.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [CFileException::m_cause](#m_cause) listę możliwych wyliczyć wartości.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]  
  
##  <a name="geterrormessage"></a>  CFileException::GetErrorMessage  
 Pobiera tekst opisujący wyjątek.  
  
```  
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,  
    UINT nMaxError,  
    PUINT pnHelpContext = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [w, out] *lpszError*  
 Wskaźnik do buforu, który odbiera komunikat o błędzie.  
  
 [in] *nMaxError*  
 Maksymalna liczba znaków, które może przechowywać określony bufor. Obejmuje to znak końcowy null.  
  
 [w, out] *pnHelpContext*  
 Wskaźnik na liczbę całkowitą bez znaku, odbierająca identyfikator pomocy kontekstu. Jeśli `NULL`, zwracany jest brak Identyfikatora.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli metoda zakończyło się pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli określony bufor jest za mały, komunikat o błędzie zostanie obcięta.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `CFileException::GetErrorMessage`.  
  
 [!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]  
  
##  <a name="m_cause"></a>  CFileException::m_cause  
 Zawiera wartości zdefiniowanych przez `CFileException` typ wyliczeniowy.  
  
```  
int m_cause;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten element członkowski danych jest publiczny zmiennej typu **int**. Moduły wyliczające i ich znaczenie są następujące:  
  
- `CFileException::none` 0: Wystąpił błąd.  
  
- `CFileException::genericException` 1: Wystąpił nieokreślony błąd.  
  
- `CFileException::fileNotFound` 2: nie można zlokalizować pliku.  
  
- `CFileException::badPath` 3: całości lub części ścieżki jest nieprawidłowa.  
  
- `CFileException::tooManyOpenFiles` 4: dozwolona liczba otwartych plików została przekroczona.  
  
- `CFileException::accessDenied` 5: nie można uzyskać dostępu do pliku.  
  
- `CFileException::invalidFile` 6: Wystąpił próba użycia nieprawidłowe dojście do pliku.  
  
- `CFileException::removeCurrentDir` 7: nie można usunąć bieżącego katalogu roboczego.  
  
- `CFileException::directoryFull` 8: nie ma żadnych więcej wpisów w katalogu.  
  
- `CFileException::badSeek` 9: Wystąpił błąd podczas próby ustawienia wskaźnika pliku.  
  
- `CFileException::hardIO` 10: Wystąpił błąd sprzętowy.  
  
- `CFileException::sharingViolation` 11: UDZIAŁU. Nie załadowano plik EXE lub udostępniony region został zablokowany.  
  
- `CFileException::lockViolation` 12: próbę zablokować region, który był już zablokowany.  
  
- `CFileException::diskFull` 14: dysk jest pełny.  
  
- `CFileException::endOfFile` 15: Osiągnięto koniec pliku.  
  
    > [!NOTE]
    >  Te `CFileException` moduły wyliczające Przyczyna różnią się od `CArchiveException` spowodować wyliczenia.  
  
    > [!NOTE]
    > `CArchiveException::generic` jest przestarzały. Zamiast nich należy używać słów kluczowych `genericException`. Jeśli `generic` jest używane w aplikacji i skompilowanej za pomocą/CLR, wynikową składnię błędów nie są łatwe do odszyfrowania.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]  
  
##  <a name="m_loserror"></a>  CFileException::m_lOsError  
 Zawiera kod błędu systemu operacyjnego dla tego wyjątku.  
  
```  
LONG m_lOsError;  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz instrukcji obsługi technicznej systemu operacyjnego zawiera listę kodów błędów. Ten element członkowski danych jest publiczny zmiennej typu **DŁUGI**.  
  
##  <a name="m_strfilename"></a>  CFileException::m_strFileName  
 Zawiera nazwę pliku dla tego warunku wyjątku.  
  
```  
CString m_strFileName;  
```  
  
##  <a name="oserrortoexception"></a>  CFileException::OsErrorToException  
 Zwraca moduł wyliczający, który odpowiada danym *lOsError* wartości. Jeśli kod błędu jest nieznany, a następnie funkcja zwraca **CFileException::generic**.  
  
```  
static int PASCAL OsErrorToException(LONG lOsError);
```  
  
### <a name="parameters"></a>Parametry  
 *lOsError*  
 Działania systemu — kod błędu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość wyliczeniowa odpowiada wartości danego błędu systemu operacyjnego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]  
  
##  <a name="throwerrno"></a>  CFileException::ThrowErrno  
 Konstruuje `CFileException` obiektu odpowiadającego danego *nErrno* wartości, a następnie zgłasza wyjątek.  
  
```  
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *nErrno*  
 Kod błędu całkowitą zgodnie z definicją w pliku dołączanego środowiska wykonawczego numer błędu. H.  
  
 *lpszFileName*  
 Wskaźnik do ciągu zawierającego nazwę pliku, który spowodował wyjątek, jeśli jest dostępna.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]  
  
##  <a name="throwoserror"></a>  CFileException::ThrowOsError  
 Zgłasza wyjątek `CFileException` odpowiadającego danego *lOsError* wartości. Jeśli kod błędu jest nieznany, a następnie funkcja zgłasza wyjątek zakodowane jako **CFileException::generic**.  
  
```  
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lOsError*  
 Działania systemu — kod błędu.  
  
 *lpszFileName*  
 Wskaźnik do ciągu zawierającego nazwę pliku, który spowodował wyjątek, jeśli jest dostępna.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Cexception — klasa](../../mfc/reference/cexception-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Przetwarzanie wyjątków](../../mfc/reference/exception-processing.md)



