---
title: "Cexception — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CException
- AFX/CException
- AFX/CException::CException
- AFX/CException::Delete
- AFX/CException::ReportError
dev_langs: C++
helpviewer_keywords:
- CException [MFC], CException
- CException [MFC], Delete
- CException [MFC], ReportError
ms.assetid: cfacf14d-bfe4-4666-a5c7-38b800512920
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 15037544b3344f5d43ebaa34fb35b431da581593
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cexception-class"></a>Cexception — klasa
Klasa podstawowa dla wszystkich wyjątków w Microsoft Foundation Class Library.  
  
## <a name="syntax"></a>Składnia  
  
```  
class AFX_NOVTABLE CException : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CException::CException](#cexception)|Konstruuje `CException` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CException::Delete](#delete)|Usuwa `CException` obiektu.|  
|[CException::ReportError](#reporterror)|Raporty komunikat o błędzie w oknie komunikatu dla użytkownika.|  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ `CException` jest abstrakcyjna klasa podstawowa nie można utworzyć `CException` obiektów bezpośrednio; należy utworzyć obiekty klas pochodnych. Jeśli musisz utworzyć własne `CException`— styl klasy, należy użyć jednej z klas pochodnych wymienionych powyżej jako model. Upewnij się, że w klasie pochodnej również używa `IMPLEMENT_DYNAMIC`.  
  
 Klasy pochodne i ich opisy są wymienione poniżej:  
  
|||  
|-|-|  
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|Klasa podstawowa dla zasobu o znaczeniu krytycznym wyjątków MFC|  
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|Nieprawidłowy argument warunku wyjątku|  
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|Wyjątek braku pamięci|  
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Żądanie dla nieobsługiwanej operacji|  
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|Wyjątków specyficzne dla archiwum|  
|[CFileException](../../mfc/reference/cfileexception-class.md)|Wyjątków specyficzne dla pliku|  
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|Zasobów systemu Windows nie została odnaleziona lub nie możliwość utworzenia|  
|[COleException](../../mfc/reference/coleexception-class.md)|Wyjątek OLE|  
|[CDBException](../../mfc/reference/cdbexception-class.md)|Wyjątek bazy danych (czyli wyjątek warunki wynikające dla klas baz danych MFC Otwórz połączenie z bazą danych w oparciu)|  
|[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|Wyjątek alokacji (automatyzacji) OLE|  
|[CUserException](../../mfc/reference/cuserexception-class.md)|Wyjątek, który wskazuje, że nie można odnaleźć zasobu|  
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|Obiekt wyjątku (oznacza to, że wyjątek warunki wynikających dla klasy DAO) dostępu do danych|  
|[CInternetException](../../mfc/reference/cinternetexception-class.md)|Wyjątek Internet (to znaczy wyjątek warunki wynikających dla klasy internetowe).|  
  
 Te wyjątki są przeznaczone do użycia z [THROW](exception-processing.md#throw), [throw_last —](exception-processing.md#throw_last), [spróbuj](exception-processing.md#try), [catch](exception-processing.md#catch), [and_catch —](exception-processing.md#and_catch), i [end_catch —](exception-processing.md#end_catch) makra. Aby uzyskać więcej informacji dotyczących wyjątków, zobacz [przetwarzania wyjątek](exception-processing.md), lub zobacz artykuł [obsługi wyjątków (MFC)](../exception-handling-in-mfc.md).  
  
 Aby wykryć określony wyjątek, użyj odpowiedniej klasy pochodnej. Catch wszystkich typów wyjątków, użyj `CException`, a następnie użyć [CObject::IsKindOf](cobject-class.md#iskindof) rozróżnianie między `CException`-klas pochodnych. Należy pamiętać, że `CObject::IsKindOf` działa tylko w przypadku klasy zadeklarowany z [implement_dynamic —](run-time-object-model-services.md#implement_dynamic) makra, aby korzystać z typu dynamicznego sprawdzania. Wszelkie `CException`— należy użyć klasy pochodnej, który utworzono `IMPLEMENT_DYNAMIC` makra zbyt.  
  
 Szczegółowe informacje można zgłaszanie wyjątków dla użytkownika, wywołując [GetErrorMessage](cfileexception-class.md#geterrormessage) lub [funkcję ReportError](#reporterror), dwie funkcje Członkowskie, które współpracują ze wszystkimi `CException`do klas pochodnych.  
  
 Jeśli wystąpił wyjątek pojedynczo makr, `CException` automatycznie usunąć obiektu; nie należy go usuwać samodzielnie. Jeśli wystąpił wyjątek przy użyciu **catch** — słowo kluczowe, nie zostanie automatycznie usunięta. Zapoznaj się z artykułem [obsługi wyjątków (MFC)](../exception-handling-in-mfc.md) Aby uzyskać więcej informacji o tym, kiedy można usunąć obiektu z wyjątkiem.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](cobject-class.md)  
  
 `CException`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
  
##  <a name="cexception"></a>CException::CException  
 Konstruuje funkcji członkowskiej `CException` obiektu.  
  
```  
explicit CException(BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>Parametry  
 *b_AutoDelete*  
 Określ **TRUE** Jeśli pamięć `CException` obiektu przydzielone na stercie. Spowoduje to `CException` obiektu do usunięcia po **usunąć** funkcja członkowska jest wywoływana, aby usunąć wyjątku. Określ **FALSE** Jeśli `CException` na stosie lub obiektu jest obiekt globalny. W takim przypadku `CException` obiektu nie zostanie usunięte, gdy **usunąć** została wywołana funkcja elementu członkowskiego.  
  
### <a name="remarks"></a>Uwagi  
 Zwykle nigdy nie należy bezpośrednio wywoływać tego konstruktora. Funkcja, która zgłasza wyjątek, należy utworzyć wystąpienie `CException`-klasy i Wywołaj jego konstruktora lub powinien użycie MFC zgłosić funkcje, takie jak [afxthrowfileexception —](exception-processing.md#afxthrowfileexception), aby zgłosić wstępnie zdefiniowanego typu. Ta dokumentacja jest dostępna tylko dla informacje były kompletne.  
  
##  <a name="delete"></a>CException::Delete  
 Ta funkcja sprawdza, czy **cexception —** obiekt został utworzony na stosie, a jeśli tak jest, wywołuje metodę **usunąć** operator obiektu.  
  
```  
void Delete();
```  
  
### <a name="remarks"></a>Uwagi  
 Podczas usuwania **cexception —** obiektów, użyj **usunąć** funkcji członkowskiej można usunąć wyjątku. Nie używaj **usunąć** operator bezpośrednio, ponieważ `CException` obiektu może być obiektem globalnych lub zostały utworzone na stosie.  
  
 Można określić, czy obiekt powinien zostać usunięte podczas konstruowania obiektu. Aby uzyskać więcej informacji, zobacz [CException::CException](#cexception).  
  
 Należy wywołać **usunąć** Jeśli używasz języka C++ **spróbuj**- **catch** mechanizmu. Jeśli używasz makr MFC **SPRÓBUJ** i **CATCH**, następnie tych makr automatycznie spowoduje wywołanie tej funkcji.  
  
### <a name="example"></a>Przykład  
 ```cpp  
 CFile* pFile = NULL;
// Constructing a CFile object with this override may throw
// a CFile exception, and won't throw any other exceptions.
// Calling CString::Format() may throw a CMemoryException,
// so we have a catch block for such exceptions, too. Any
// other exception types this function throws will be
// routed to the calling function.
// Note that this example performs the same actions as the 
// example for CATCH, but uses C++ try/catch syntax instead
// of using the MFC TRY/CATCH macros. This sample must use
// CException::Delete() to delete the exception objects
// before closing the catch block, while the CATCH example
// implicitly performs the deletion via the macros.
try
{
   pFile = new CFile(_T("C:\\WINDOWS\\SYSTEM.INI"),
      CFile::modeRead | CFile::shareDenyNone);
   ULONGLONG ullLength = pFile->GetLength();
   CString str;
   str.Format(_T("Your SYSTEM.INI file is %u bytes long."), ullLength);
   AfxMessageBox(str);
}
catch(CFileException* pEx)
{
   // Simply show an error message to the user.
   pEx->ReportError();
   pEx->Delete();
}
catch(CMemoryException* pEx)
{
   // We can't recover from this memory exception, so we'll
   // just terminate the app without any cleanup. Normally, an
   // an application should do everything it possibly can to
   // clean up properly and _not_ call AfxAbort().
   pEx->Delete();
   AfxAbort();
}
// If an exception occurrs in the CFile constructor,
// the language will free the memory allocated by new
// and will not complete the assignment to pFile.
// Thus, our clean-up code needs to test for NULL.
if (pFile != NULL)
{
   pFile->Close();
   delete pFile;
}   
 ```
  
##  <a name="reporterror"></a>CException::ReportError  
 Wywołanie funkcji członkowskiej na tekst błędu raportu w oknie komunikatu dla użytkownika.  
  
```  
virtual int ReportError(
    UINT nType = MB_OK,  
    UINT nMessageID = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nType`  
 Określa styl okna komunikatu. Zastosuj dowolną kombinację [Style okna komunikatu](message-box-styles.md) do pola. Jeśli ten parametr nie zostanie określony, wartością domyślną jest **mb_ok —**.  
  
 *nMessageID*  
 Określa identyfikator zasobu (ciąg spisu) komunikat do wyświetlenia, jeśli obiekt wyjątku nie jest komunikat o błędzie. Jeśli jest to 0, komunikat "żaden komunikat o błędzie jest niedostępna" jest wyświetlany.  
  
### <a name="return-value"></a>Wartość zwracana  
 `AfxMessageBox` Wartości; w przeciwnym razie 0, jeśli nie ma wystarczającej ilości pamięci do wyświetlenia w oknie komunikatu. Zobacz [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) zwracanych wartości.  
  
### <a name="example"></a>Przykład  
 Oto przykład wykorzystania `CException::ReportError`. Na przykład innego, zobacz przykład [CATCH](exception-processing.md#catch).  
  
```cpp  
CFile fileInput;
CFileException ex;

// try to open a file for reading.  
// The file will certainly not
// exist because there are too many explicit
// directories in the name.

// if the call to Open() fails, ex will be
// initialized with exception
// information.  the call to ex.ReportError() will
// display an appropriate
// error message to the user, such as
// "\Too\Many\Bad\Dirs.DAT contains an
// invalid path."  The error message text will be
// appropriate for the
// file name and error condition.

if (!fileInput.Open(_T("\\Too\\Many\\Bad\\Dirs.DAT"), CFile::modeRead, &ex))
{
  ex.ReportError();
}
else
{
  // the file was opened, so do whatever work
  // with fileInput we were planning...

  fileInput.Close();
}
```

## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](cobject-class.md)   
 [Diagram hierarchii](../hierarchy-chart.md)   
 [Wyjątek podczas przetwarzania](exception-processing.md)   
 [Jak: utworzyć własne klasy wyjątków niestandardowych](http://go.microsoft.com/fwlink/linkid=128045)


