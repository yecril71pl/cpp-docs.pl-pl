---
title: Klasa COleStreamFile
ms.date: 11/04/2016
f1_keywords:
- COleStreamFile
- AFXOLE/COleStreamFile
- AFXOLE/COleStreamFile::COleStreamFile
- AFXOLE/COleStreamFile::Attach
- AFXOLE/COleStreamFile::CreateMemoryStream
- AFXOLE/COleStreamFile::CreateStream
- AFXOLE/COleStreamFile::Detach
- AFXOLE/COleStreamFile::GetStream
- AFXOLE/COleStreamFile::OpenStream
helpviewer_keywords:
- COleStreamFile [MFC], COleStreamFile
- COleStreamFile [MFC], Attach
- COleStreamFile [MFC], CreateMemoryStream
- COleStreamFile [MFC], CreateStream
- COleStreamFile [MFC], Detach
- COleStreamFile [MFC], GetStream
- COleStreamFile [MFC], OpenStream
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
ms.openlocfilehash: 1f53d3bd55fbff45257c06af2ab11f066d421a54
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376098"
---
# <a name="colestreamfile-class"></a>Klasa COleStreamFile

Reprezentuje strumień danych`IStream`( ) w pliku złożonym jako część OLE Structured Storage.

## <a name="syntax"></a>Składnia

```
class COleStreamFile : public CFile
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleStreamFile::COleStreamFile](#colestreamfile)|Konstruuje `COleStreamFile` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleStreamFile::Dołącz](#attach)|Kojarzy strumień z obiektem.|
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|Tworzy strumień z pamięci globalnej i kojarzy go z obiektem.|
|[COleStreamFile::CreateStream](#createstream)|Tworzy strumień i kojarzy go z obiektem.|
|[COleStreamFile::Detach](#detach)|Odłącza strumień od obiektu.|
|[COleStreamFile::GetStream](#getstream)|Zwraca bieżący strumień.|
|[COleStreamFile::OpenStream](#openstream)|Bezpiecznie otwiera strumień i kojarzy go z obiektem.|

## <a name="remarks"></a>Uwagi

Obiekt `IStorage` musi istnieć, zanim strumień może być otwarty lub utworzony, chyba że jest to strumień pamięci.

`COleStreamFile`obiekty są manipulowane dokładnie tak jak [obiekty CFile.](../../mfc/reference/cfile-class.md)

Aby uzyskać więcej informacji na temat manipulowania strumieniami i magazynami, zobacz artykuł [Kontenery: Pliki złożone](../../mfc/containers-compound-files.md)..

Aby uzyskać więcej informacji, zobacz [IStream](/windows/win32/api/objidl/nn-objidl-istream) i [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) w windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cfile](../../mfc/reference/cfile-class.md)

`COleStreamFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

## <a name="colestreamfileattach"></a><a name="attach"></a>COleStreamFile::Dołącz

Kojarzy dostarczony strumień OLE `COleStreamFile` z obiektem.

```
void Attach(LPSTREAM lpStream);
```

### <a name="parameters"></a>Parametry

*lpStream (strumień)*<br/>
Wskazuje strumień OLE`IStream`( ) do skojarzenia z obiektem. Nie może być null.

### <a name="remarks"></a>Uwagi

Obiekt nie może być już skojarzony ze strumieniem OLE.

Aby uzyskać więcej informacji, zobacz [IStream](/windows/win32/api/objidl/nn-objidl-istream) w windows SDK.

## <a name="colestreamfilecolestreamfile"></a><a name="colestreamfile"></a>COleStreamFile::COleStreamFile

Tworzy obiekt `COleStreamFile`.

```
COleStreamFile(LPSTREAM lpStream = NULL);
```

### <a name="parameters"></a>Parametry

*lpStream (strumień)*<br/>
Wskaźnik do strumienia OLE, który ma być skojarzony z obiektem.

### <a name="remarks"></a>Uwagi

Jeśli *lpStream* ma wartość NULL, obiekt nie jest skojarzony ze strumieniem OLE, w przeciwnym razie obiekt jest skojarzony z dostarczonym strumieniem OLE.

Aby uzyskać więcej informacji, zobacz [IStream](/windows/win32/api/objidl/nn-objidl-istream) w windows SDK.

## <a name="colestreamfilecreatememorystream"></a><a name="creatememorystream"></a>COleStreamFile::CreateMemoryStream

Bezpiecznie tworzy nowy strumień z globalnej, udostępnionej pamięci, gdzie błąd jest normalnym, oczekiwanym warunkiem.

```
BOOL CreateMemoryStream(CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*Perror*<br/>
Wskazuje [obiekt CFileException](../../mfc/reference/cfileexception-class.md) lub NULL, który wskazuje stan zakończenia operacji tworzenia. Podaj ten parametr, jeśli chcesz monitorować możliwe wyjątki generowane przez próbę utworzenia strumienia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli strumień został utworzony pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pamięć jest przydzielana przez podsystem OLE.

Aby uzyskać więcej informacji, zobacz [CreateStreamOnHGlobal](/windows/win32/api/combaseapi/nf-combaseapi-createstreamonhglobal) w windows SDK.

## <a name="colestreamfilecreatestream"></a><a name="createstream"></a>COleStreamFile::CreateStream

Bezpiecznie tworzy nowy strumień w dostarczonym obiekcie magazynu, gdzie błąd jest normalnym, oczekiwanym warunkiem.

```
BOOL CreateStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*lpStorage*<br/>
Wskazuje obiekt magazynu OLE, który zawiera strumień, który ma zostać utworzony. Nie może być null.

*lpszStreamName (Nazwa)*<br/>
Nazwa strumienia, który ma zostać utworzony. Nie może być null.

*nOpenLags*<br/>
Tryb dostępu do użycia podczas otwierania strumienia. Tryby wyłączności, odczytu/zapisu i tworzenia są używane domyślnie. Aby uzyskać pełną listę dostępnych trybów, zobacz [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).

*Perror*<br/>
Wskazuje obiekt [CFileException](../../mfc/reference/cfileexception-class.md) lub NULL. Podaj ten parametr, jeśli chcesz monitorować możliwe wyjątki generowane przez próbę utworzenia strumienia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli strumień został utworzony pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wyjątek pliku zostanie zgłoszony, jeśli open nie powiedzie się, a *pError* nie ma wartości NULL.

Aby uzyskać więcej informacji, zobacz [IStorage::CreateStream](/windows/win32/api/objidl/nf-objidl-istorage-createstream) w usłudze Windows SDK.

## <a name="colestreamfiledetach"></a><a name="detach"></a>COleStreamFile::Detach

Disassociates strumienia z obiektu bez zamykania strumienia.

```
LPSTREAM Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do strumienia`IStream`( ), który został skojarzony z obiektem.

### <a name="remarks"></a>Uwagi

Strumień musi zostać zamknięty w inny sposób przed zakończeniem programu.

Aby uzyskać więcej informacji, zobacz [IStream](/windows/win32/api/objidl/nn-objidl-istream) w windows SDK.

## <a name="colestreamfilegetstream"></a><a name="getstream"></a>COleStreamFile::GetStream

Wywołanie tej funkcji, aby powrócić wskaźnik do bieżącego strumienia.

```
IStream* GetStream() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bieżącego interfejsu strumienia ( [IStream](/windows/win32/api/objidl/nn-objidl-istream)).

## <a name="colestreamfileopenstream"></a><a name="openstream"></a>COleStreamFile::OpenStream

Otwiera istniejący strumień.

```
BOOL OpenStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*lpStorage*<br/>
Wskazuje obiekt pamięci masowej OLE zawierający strumień, który ma zostać otwarty. Nie może być null.

*lpszStreamName (Nazwa)*<br/>
Nazwa strumienia, który ma zostać otwarty. Nie może być null.

*nOpenLags*<br/>
Tryb dostępu do użycia podczas otwierania strumienia. Tryby wyłączności i odczytu/zapisu są używane domyślnie. Aby uzyskać pełną listę dostępnych trybów, zobacz [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).

*Perror*<br/>
Wskazuje obiekt [CFileException](../../mfc/reference/cfileexception-class.md) lub NULL. Podaj ten parametr, jeśli chcesz monitorować możliwe wyjątki generowane przez próbę otwarcia strumienia.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli strumień jest otwarty pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wyjątek pliku zostanie zgłoszony, jeśli open nie powiedzie się, a *pError* nie ma wartości NULL.

Aby uzyskać więcej informacji, zobacz [IStorage::OpenStream](/windows/win32/api/objidl/nf-objidl-istorage-openstream) w usłudze Windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa CFile](../../mfc/reference/cfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
