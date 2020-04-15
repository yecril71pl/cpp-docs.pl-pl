---
title: Klasa CException
ms.date: 11/04/2016
f1_keywords:
- CException
- AFX/CException
- AFX/CException::CException
- AFX/CException::Delete
- AFX/CException::ReportError
helpviewer_keywords:
- CException [MFC], CException
- CException [MFC], Delete
- CException [MFC], ReportError
ms.assetid: cfacf14d-bfe4-4666-a5c7-38b800512920
ms.openlocfilehash: c3742db7475e626b18e9c073a0b7417a8034863f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373940"
---
# <a name="cexception-class"></a>Klasa CException

Klasa podstawowa dla wszystkich wyjątków w bibliotece klas Programu Microsoft Foundation.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE CException : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CException::CException](#cexception)|Konstruuje `CException` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CException::Delete](#delete)|Usuwa `CException` obiekt.|
|[CException::ReportError](#reporterror)|Zgłasza użytkownikowi komunikat o błędzie w oknie komunikatu.|

## <a name="remarks"></a>Uwagi

Ponieważ `CException` jest abstrakcyjną klasą `CException` podstawową, nie można tworzyć obiektów bezpośrednio; należy utworzyć obiekty klas pochodnych. Jeśli chcesz utworzyć własną `CException`klasę -style, użyj jednej z klas pochodnych wymienionych powyżej jako modelu. Upewnij się, że klasa pochodna również używa `IMPLEMENT_DYNAMIC`.

Klasy pochodne i ich opisy są wymienione poniżej:

|||
|-|-|
|[Csimpleexception](../../mfc/reference/csimpleexception-class.md)|Klasa podstawowa dla wyjątków MFC o krytycznym znaczeniu dla zasobów|
|[CInvalidArgWynienie](../../mfc/reference/cinvalidargexception-class.md)|Warunek wyjątku nieprawidłowego argumentu|
|[Cmemoryexception](../../mfc/reference/cmemoryexception-class.md)|Wyjątek braku pamięci|
|[Cnotsupportedexception](../../mfc/reference/cnotsupportedexception-class.md)|Żądanie nieobsługiwało operacji|
|[Carchiveexception](../../mfc/reference/carchiveexception-class.md)|Wyjątek specyficzny dla archiwum|
|[Cfileexception](../../mfc/reference/cfileexception-class.md)|Wyjątek specyficzny dla pliku|
|[CResourceException (Nieeksouracja)](../../mfc/reference/cresourceexception-class.md)|Nie znaleziono lub nie można utworzyć zasobu systemu Windows|
|[Coleexception](../../mfc/reference/coleexception-class.md)|Wyjątek OLE|
|[Cdbexception](../../mfc/reference/cdbexception-class.md)|Wyjątek bazy danych (czyli warunki wyjątków powstające dla klas bazy danych MFC na podstawie łączności otwartej bazy danych)|
|[COleDispatchWycję](../../mfc/reference/coledispatchexception-class.md)|Wyjątek (automatyzacja) wysyłki OLE|
|[CUserException](../../mfc/reference/cuserexception-class.md)|Wyjątek wskazujący, że nie można odnaleźć zasobu|
|[Cdaoexception](../../mfc/reference/cdaoexception-class.md)|Wyjątek obiektu dostępu do danych (czyli warunki wyjątku powstające dla klas DAO)|
|[Cinternetexception](../../mfc/reference/cinternetexception-class.md)|Wyjątek internetowy (czyli warunki wyjątku powstające dla klas internetowych).|

Wyjątki te są przeznaczone do użycia z [makrami THROW](exception-processing.md#throw), [THROW_LAST](exception-processing.md#throw_last), [try](exception-processing.md#try), [catch](exception-processing.md#catch), [and_catch](exception-processing.md#and_catch)i [end_catch.](exception-processing.md#end_catch) Aby uzyskać więcej informacji na temat wyjątków, zobacz [Przetwarzanie wyjątków](exception-processing.md)lub zobacz artykuł [Obsługa wyjątków (MFC)](../exception-handling-in-mfc.md).

Aby złapać określony wyjątek, należy użyć odpowiedniej klasy pochodnej. Aby wychwytywać wszystkie `CException`typy wyjątków, należy użyć , a następnie `CException`użyć [CObject::IsKindOf](cobject-class.md#iskindof) do rozróżniania klas pochodnych. Należy `CObject::IsKindOf` zauważyć, że działa tylko dla klas zadeklarowanych z [makrą IMPLEMENT_DYNAMIC,](run-time-object-model-services.md#implement_dynamic) aby skorzystać z dynamicznego sprawdzania typu. Każda `CException`utworzona klasa pochodna powinna `IMPLEMENT_DYNAMIC` również używać makra.

Można zgłosić szczegóły dotyczące wyjątków dla użytkownika, wywołując [GetErrorMessage](cfileexception-class.md#geterrormessage) lub [ReportError](#reporterror), dwie funkcje członkowskie, które działają z dowolnej `CException`klasy pochodnej.

Jeśli wyjątek zostanie przechwycony przez jedno `CException` z makr, obiekt zostanie automatycznie usunięty; nie usuwaj go samodzielnie. Jeśli wyjątek zostanie przechwycony przy użyciu **catch** słowa kluczowego, nie jest automatycznie usuwany. Zobacz artykuł [Obsługa wyjątków (MFC),](../exception-handling-in-mfc.md) aby uzyskać więcej informacji na temat tego, kiedy usunąć obiekt exeption.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](cobject-class.md)

`CException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="cexceptioncexception"></a><a name="cexception"></a>CException::CException

Ta funkcja elementu `CException` członkowskiego konstruuje obiekt.

```
explicit CException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Parametry

*b_AutoDelete*<br/>
Określ wartość PRAWDA, `CException` jeśli pamięć dla obiektu została przydzielona na stercie. Spowoduje to, `CException` że obiekt zostanie `Delete` usunięty, gdy funkcja elementu członkowskiego jest wywoływana, aby usunąć wyjątek. Określ wartość `CException` FAŁSZ, jeśli obiekt znajduje się na stosie lub jest obiektem globalnym. W takim przypadku `CException` obiekt nie zostanie `Delete` usunięty, gdy wywoływana jest funkcja elementu członkowskiego.

### <a name="remarks"></a>Uwagi

Zwykle nigdy nie trzeba wywołać tego konstruktora bezpośrednio. Funkcja, która zgłasza wyjątek należy utworzyć `CException`wystąpienie klasy pochodnej i wywołać jego konstruktora lub należy użyć jednej z funkcji MFC throw, takich jak [AfxThrowFileException](exception-processing.md#afxthrowfileexception), aby rzucić wstępnie zdefiniowany typ. Ta dokumentacja jest dostarczana tylko dla kompletności.

## <a name="cexceptiondelete"></a><a name="delete"></a>CException::Delete

Ta funkcja sprawdza, `CException` czy obiekt został utworzony na stercie, a jeśli tak, wywołuje **delete** operator na obiekcie.

```
void Delete();
```

### <a name="remarks"></a>Uwagi

Podczas usuwania `CException` obiektu należy `Delete` użyć funkcji elementu członkowskiego, aby usunąć wyjątek. Nie należy używać **delete** operator bezpośrednio, ponieważ `CException` obiekt może być obiekt globalny lub zostały utworzone na stosie.

Można określić, czy obiekt ma zostać usunięty podczas konstruowania obiektu. Aby uzyskać więcej informacji, zobacz [CException::CException](#cexception).

Wystarczy wywołać `Delete` tylko wtedy, gdy używasz mechanizmu**catch** **try**- języka C++. Jeśli używasz makr MFC **TRY** i **CATCH,** te makra automatycznie wywołają tę funkcję.

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

## <a name="cexceptionreporterror"></a><a name="reporterror"></a>CException::ReportError

Wywołanie tej funkcji elementu członkowskiego, aby zgłosić tekst błędu w oknie komunikatu do użytkownika.

```
virtual int ReportError(
    UINT nType = MB_OK,
    UINT nMessageID = 0);
```

### <a name="parameters"></a>Parametry

*nTyp*<br/>
Określa styl okna komunikatu. Zastosuj dowolną kombinację [stylów pola wiadomości](styles-used-by-mfc.md#message-box-styles) do pola. Jeśli ten parametr nie zostanie określony, wartość domyślna to MB_OK.

*nMessageID*<br/>
Określa identyfikator zasobu (wpis tabeli ciągów) komunikatu do wyświetlenia, jeśli obiekt wyjątku nie ma komunikatu o błędzie. Jeśli 0, zostanie wyświetlony komunikat "Nie jest dostępny komunikat o błędzie".

### <a name="return-value"></a>Wartość zwracana

Wartość; `AfxMessageBox` w przeciwnym razie 0, jeśli nie ma wystarczającej ilości pamięci, aby wyświetlić okno komunikatu. Zobacz [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) dla możliwych wartości zwracanych.

### <a name="example"></a>Przykład

Oto przykład użycia `CException::ReportError`. Inny przykład można znaleźć w przykładzie [catch](exception-processing.md#catch).

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

[Klasa CObject](cobject-class.md)<br/>
[Wykres hierarchii](../hierarchy-chart.md)<br/>
[Przetwarzanie wyjątków](exception-processing.md)<br/>
[Jak: Tworzenie własnych niestandardowych klas wyjątków](https://go.microsoft.com/fwlink/p/?linkid=128045)
