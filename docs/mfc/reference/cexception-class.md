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
ms.openlocfilehash: e27802e05c832d28d848d9eb1235d6ef5980b306
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841561"
---
# <a name="cexception-class"></a>Klasa CException

Klasa bazowa dla wszystkich wyjątków w biblioteka MFC.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE CException : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CException:: CException](#cexception)|Konstruuje `CException` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CException::D Usuń](#delete)|Usuwa `CException` obiekt.|
|[CException:: ReportError](#reporterror)|Wyświetla komunikat o błędzie w oknie komunikatu dla użytkownika.|

## <a name="remarks"></a>Uwagi

Ponieważ `CException` jest abstrakcyjną klasą bazową, nie można `CException` bezpośrednio tworzyć obiektów; należy utworzyć obiekty klas pochodnych. Jeśli musisz utworzyć własną `CException` klasę stylu, użyj jednej z klas pochodnych wymienionych powyżej jako model. Upewnij się, że Klasa pochodna również używa `IMPLEMENT_DYNAMIC` .

Poniżej wymieniono klasy pochodne i ich opisy:

|Nazwa|Opis|
|-|-|
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|Klasa bazowa dla wyjątków MFC o krytycznym poziomie zasobów|
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|Nieprawidłowy warunek wyjątku argumentu|
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|Wyjątek braku pamięci|
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Żądanie nieobsługiwanej operacji|
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|Wyjątek specyficzny dla archiwalnego|
|[CFileException](../../mfc/reference/cfileexception-class.md)|Wyjątek specyficzny dla pliku|
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|Nie znaleziono zasobu systemu Windows lub nie można go uzyskać|
|[COleException](../../mfc/reference/coleexception-class.md)|Wyjątek OLE|
|[CDBException](../../mfc/reference/cdbexception-class.md)|Wyjątek bazy danych (czyli warunki wyjątków dotyczące klas baz danych MFC opartych na Open Database Connectivity)|
|[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|Wyjątek wysyłania OLE (Automation)|
|[CUserException](../../mfc/reference/cuserexception-class.md)|Wyjątek wskazujący, że nie można znaleźć zasobu|
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|Wyjątek obiektu dostępu do danych (czyli warunki wyjątków dotyczące klas DAO)|
|[CInternetException](../../mfc/reference/cinternetexception-class.md)|Wyjątek internetowy (czyli warunki wyjątków związane z klasami internetowymi).|

Te wyjątki są przeznaczone do użycia z makrami [throw](exception-processing.md#throw), [THROW_LAST](exception-processing.md#throw_last), [try](exception-processing.md#try), [catch](exception-processing.md#catch), [AND_CATCH](exception-processing.md#and_catch)i [END_CATCH](exception-processing.md#end_catch) . Aby uzyskać więcej informacji o wyjątkach, zobacz [Przetwarzanie wyjątków](exception-processing.md)lub zapoznaj się z [obsługą wyjątków artykułów (MFC)](../exception-handling-in-mfc.md).

Aby przechwytywać konkretny wyjątek, użyj odpowiedniej klasy pochodnej. Aby wychwycić wszystkie typy wyjątków, użyj `CException` , a następnie użyj [CObject:: IsKindOf](cobject-class.md#iskindof) , aby rozróżnić `CException` klasy pochodne. Należy pamiętać, że `CObject::IsKindOf` działa tylko dla klas zadeklarowanych za pomocą makra [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic) , aby można było korzystać z sprawdzania typu dynamicznego. `CException`Utworzona klasa pochodna powinna `IMPLEMENT_DYNAMIC` również używać makra.

Możesz zgłosić szczegółowe informacje o wyjątkach dla użytkownika, wywołując [GetErrorMessage](cfileexception-class.md#geterrormessage) lub [ReportError](#reporterror), dwie funkcje członkowskie, które działają z dowolnymi `CException` klasami pochodnymi.

Jeśli wyjątek jest przechwytywany przez jeden z makr, `CException` obiekt zostanie usunięty automatycznie; nie należy go usuwać. Jeśli wyjątek jest przechwytywany przy użyciu **`catch`** słowa kluczowego, nie jest automatycznie usuwany. Zapoznaj się z tematem [Obsługa wyjątków artykułów (MFC)](../exception-handling-in-mfc.md) , aby uzyskać więcej informacji na temat sytuacji, w których należy usunąć obiekt exeption.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](cobject-class.md)

`CException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

## <a name="cexceptioncexception"></a><a name="cexception"></a> CException:: CException

Ta funkcja członkowska konstruuje `CException` obiekt.

```
explicit CException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Parametry

*b_AutoDelete*<br/>
Określ wartość TRUE, jeśli pamięć dla `CException` obiektu została przypisana na stercie. Spowoduje to `CException` usunięcie obiektu, gdy `Delete` wywoływana jest funkcja członkowska, aby usunąć wyjątek. Określ wartość FAŁSZ, jeśli `CException` obiekt znajduje się na stosie lub jest obiektem globalnym. W takim przypadku `CException` obiekt nie zostanie usunięty, gdy `Delete` wywoływana jest funkcja członkowska.

### <a name="remarks"></a>Uwagi

Zwykle nigdy nie trzeba wywoływać tego konstruktora bezpośrednio. Funkcja, która zgłasza wyjątek, powinna utworzyć wystąpienie `CException` klasy pochodnej i wywołać jej konstruktora lub użyć jednej z funkcji Throw MFC, takich jak [AfxThrowFileException](exception-processing.md#afxthrowfileexception), aby zgłosić wstępnie zdefiniowany typ. Ta dokumentacja jest dostępna tylko w celu zapewnienia kompletności.

## <a name="cexceptiondelete"></a><a name="delete"></a> CException::D Usuń

Ta funkcja sprawdza, czy `CException` obiekt został utworzony na stercie i jeśli tak, wywołuje **`delete`** operator dla obiektu.

```cpp
void Delete();
```

### <a name="remarks"></a>Uwagi

Podczas usuwania `CException` obiektu należy użyć `Delete` funkcji elementu członkowskiego, aby usunąć wyjątek. Nie używaj **`delete`** operatora bezpośrednio, ponieważ `CException` obiekt może być obiektem globalnym lub został utworzony na stosie.

Można określić, czy obiekt ma zostać usunięty podczas konstruowania obiektu. Aby uzyskać więcej informacji, zobacz [CException:: CException](#cexception).

Musisz wywołać tylko w `Delete` przypadku korzystania z mechanizmu języka C++ **`try`** -  **`catch`** . W przypadku korzystania z makr MFC **spróbuj** i **Przechwyć**te makra będą automatycznie wywoływały tę funkcję.

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

## <a name="cexceptionreporterror"></a><a name="reporterror"></a> CException:: ReportError

Wywołaj tę funkcję elementu członkowskiego, aby zgłosić tekst błędu w oknie komunikatu do użytkownika.

```
virtual int ReportError(
    UINT nType = MB_OK,
    UINT nMessageID = 0);
```

### <a name="parameters"></a>Parametry

*Npowiadomienia*<br/>
Określa styl okna komunikatu. Zastosuj dowolną kombinację [stylów okna komunikatu](styles-used-by-mfc.md#message-box-styles) do pola. Jeśli ten parametr nie jest określony, wartość domyślna to MB_OK.

*nMessageID*<br/>
Określa identyfikator zasobu (wpis tabeli ciągów) wiadomości, która ma być wyświetlana, jeśli obiekt wyjątku nie ma komunikatu o błędzie. Jeśli wartość jest równa 0, zostanie wyświetlony komunikat "Brak dostępnego komunikatu o błędzie".

### <a name="return-value"></a>Wartość zwracana

`AfxMessageBox`Wartość; w przeciwnym razie, jeśli nie ma wystarczającej ilości pamięci, aby wyświetlić okno komunikatu. Zobacz [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) , aby uzyskać możliwe wartości zwracane.

### <a name="example"></a>Przykład

Oto przykład użycia `CException::ReportError` . W innym przykładzie zapoznaj się z przykładem [catch](exception-processing.md#catch).

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
[Przetwarzanie wyjątku](exception-processing.md)<br/>
[Jak: tworzenie własnych niestandardowych klas wyjątków](https://go.microsoft.com/fwlink/p/?linkid=128045)
