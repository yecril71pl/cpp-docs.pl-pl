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
ms.openlocfilehash: 5942e636809e3758f34d209a3da80f0d903ab708
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450357"
---
# <a name="cexception-class"></a>Klasa CException

Klasa bazowa dla wszystkich wyjątków w bibliotece klas Microsoft Foundation.

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

Ponieważ `CException` jest abstrakcyjna klasa bazowa nie można utworzyć `CException` obiektów bezpośrednio; musi utworzyć obiekty w klasach pochodnych. Jeśli musisz utworzyć własne `CException`-stylu klasy, należy użyć jednej z klas pochodnych wymienionych powyżej jako model. Upewnij się, że klasy pochodnej używa również `IMPLEMENT_DYNAMIC`.

Klasy pochodne oraz ich opisy znajdują się poniżej:

|||
|-|-|
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|Klasa bazowa dla wyjątków MFC ważnych dla zasobów|
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|Wyjątek warunku nieprawidłowego argumentu|
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|Wyjątek braku pamięci|
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Żądanie nieobsługiwaną operację|
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|Wyjątków specyficzne dla archiwum|
|[CFileException](../../mfc/reference/cfileexception-class.md)|Wyjątek specyficzne dla pliku|
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|Windows zasób nie został znaleziony lub nie możliwe do utworzenia|
|[COleException](../../mfc/reference/coleexception-class.md)|Wyjątek OLE|
|[CDBException](../../mfc/reference/cdbexception-class.md)|Wyjątek bazy danych (czyli warunków wyjątków wynikające dla klas baz danych MFC w oparciu o Open Database Connectivity)|
|[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|Wyjątek wysyłania (automatyzacji) OLE|
|[CUserException](../../mfc/reference/cuserexception-class.md)|Wyjątek, który wskazuje, że nie można odnaleźć zasobu|
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|Wyjątek do obiektu dostępu do danych (czyli warunków wyjątków wynikające dla klas DAO)|
|[CInternetException](../../mfc/reference/cinternetexception-class.md)|Wyjątek Internet (czyli warunków wyjątków wynikających dla klasy internetowe).|

Wyjątki te są przeznaczone do użycia z [THROW](exception-processing.md#throw), [THROW_LAST](exception-processing.md#throw_last), [spróbuj](exception-processing.md#try), [catch](exception-processing.md#catch), [and_catch](exception-processing.md#and_catch), i [end_catch](exception-processing.md#end_catch) makra. Aby uzyskać więcej informacji na temat wyjątków, zobacz [przetwarzania wyjątek](exception-processing.md), lub zapoznaj się z artykułem [obsługi wyjątków (MFC)](../exception-handling-in-mfc.md).

Aby przechwycić określony wyjątek, należy użyć odpowiedniej klasy pochodnej. Aby catch, wszystkie rodzaje wyjątków, należy użyć `CException`, a następnie użyj [CObject::IsKindOf](cobject-class.md#iskindof) do rozróżniania między `CException`-klasy pochodne. Należy pamiętać, że `CObject::IsKindOf` działa tylko w przypadku klasy zadeklarowane za pomocą [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic) makra, aby można było korzystać z zalet Sprawdzanie typu dynamicznego. Wszelkie `CException`— należy użyć klasy pochodnej, którą tworzysz `IMPLEMENT_DYNAMIC` makro, zbyt.

Możesz zgłosić szczegółowe informacje o wyjątkach do użytkownika, wywołując [GetErrorMessage](cfileexception-class.md#geterrormessage) lub [funkcję ReportError](#reporterror), dwie funkcje Członkowskie, które współpracują z dowolnego z `CException`w klasach pochodnych.

Jeśli wyjątek zostaje przechwycony przez jedną z makr, `CException` obiekt zostanie automatycznie usunięty; nie należy usuwać je samodzielnie. Jeśli wystąpił wyjątek przy użyciu **catch** — słowo kluczowe, nie zostanie automatycznie usunięta. Zapoznaj się z artykułem [obsługi wyjątków (MFC)](../exception-handling-in-mfc.md) Aby uzyskać więcej informacji o tym, kiedy można usunąć obiektu wyjątku.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](cobject-class.md)

`CException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="cexception"></a>  CException::CException

Ta funkcja elementu członkowskiego tworzy `CException` obiektu.

```
explicit CException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Parametry

*b_AutoDelete*<br/>
Określ wartość PRAWDA, jeśli pamięć `CException` obiektów została przydzielona na stosie. Spowoduje to `CException` obiekt do usunięcia podczas `Delete` funkcja członkowska jest wywoływana, aby usunąć wyjątku. Określ wartość FALSE, jeśli `CException` jest na stosie obiektu lub obiektów globalnych. W tym przypadku `CException` obiekt nie będą usuwane, gdy `Delete` funkcja członkowska jest wywoływana.

### <a name="remarks"></a>Uwagi

Zwykle nigdy nie należy bezpośrednio wywołania tego konstruktora. Funkcja, która zgłasza wyjątek, należy utworzyć wystąpienie `CException`-klasę pochodną i wywołać jej konstruktora lub jest on powinien użycie MFC zgłosić funkcje, takie jak [afxthrowfileexception —](exception-processing.md#afxthrowfileexception), aby zgłosić wstępnie zdefiniowanego typu. Ta dokumentacja jest dostępna tylko dla informacje były kompletne.

##  <a name="delete"></a>  CException::Delete

Ta funkcja sprawdza, czy `CException` obiekt został utworzony na stercie, a jeśli tak jest, wywołuje metodę **Usuń** operatora w obiekcie.

```
void Delete();
```

### <a name="remarks"></a>Uwagi

Podczas usuwania `CException` obiektu, należy użyć `Delete` funkcja elementu członkowskiego, można usunąć wyjątku. Nie używaj **Usuń** operator bezpośrednio, ponieważ `CException` obiektu może być obiekt globalny, lub zostały utworzone na stosie.

Można określić, czy obiekt powinien zostać usunięty, gdy obiekt jest konstruowany. Aby uzyskać więcej informacji, zobacz [CException::CException](#cexception).

Musisz wywołać `Delete` korzystania z C++ **spróbuj**- **catch** mechanizm. Jeśli używasz makr MFC **SPRÓBUJ** i **CATCH**, te makra automatycznie wywoła tę funkcję, a następnie.

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

##  <a name="reporterror"></a>  CException::ReportError

Wywołaj tę funkcję elementu członkowskiego, aby raport tekst błędu w oknie komunikatu dla użytkownika.

```
virtual int ReportError(
    UINT nType = MB_OK,
    UINT nMessageID = 0);
```

### <a name="parameters"></a>Parametry

*nType*<br/>
Określa styl okna komunikatu. Zastosuj dowolną kombinację [Style okna komunikatu](styles-used-by-mfc.md#message-box-styles) do pola. Jeśli ten parametr nie jest określony, wartość domyślna to MB_OK.

*nMessageID*<br/>
Określa identyfikator zasobu (ciąg spisu) komunikat wyświetlany, jeśli obiekt wyjątku nie jest komunikat o błędzie. Jeśli jest to 0, komunikat "bez komunikatu o błędzie jest dostępna" jest wyświetlany.

### <a name="return-value"></a>Wartość zwracana

`AfxMessageBox` Wartość; w przeciwnym razie 0, jeśli nie ma wystarczającej ilości pamięci, aby wyświetlić okno komunikatu. Zobacz [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) dla możliwych wartości zwracanych.

### <a name="example"></a>Przykład

Oto przykład wykorzystania `CException::ReportError`. Inny przykład, zobacz przykład [CATCH](exception-processing.md#catch).

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

## <a name="see-also"></a>Zobacz także

[Klasa CObject](cobject-class.md)<br/>
[Wykres hierarchii](../hierarchy-chart.md)<br/>
[Przetwarzanie wyjątków](exception-processing.md)<br/>
[Jak mogę Tworzenie własnych klas wyjątków niestandardowych](https://go.microsoft.com/fwlink/p/?linkid=128045)
