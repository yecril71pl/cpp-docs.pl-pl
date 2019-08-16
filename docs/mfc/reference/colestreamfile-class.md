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
ms.openlocfilehash: 96e8fee71f02ea750fd8b33f41fd2fd517e9081e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503685"
---
# <a name="colestreamfile-class"></a>Klasa COleStreamFile

Przedstawia strumień danych (`IStream`) w pliku złożonym w ramach magazynu strukturalnego OLE.

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
|[COleStreamFile::Attach](#attach)|Kojarzy strumień z obiektem.|
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|Tworzy strumień z pamięci globalnej i kojarzy go z obiektem.|
|[COleStreamFile::CreateStream](#createstream)|Tworzy strumień i kojarzy go z obiektem.|
|[COleStreamFile::Detach](#detach)|Usuwa strumień z obiektu.|
|[COleStreamFile::GetStream](#getstream)|Zwraca bieżący strumień.|
|[COleStreamFile::OpenStream](#openstream)|Bezpiecznie otwiera strumień i kojarzy go z obiektem.|

## <a name="remarks"></a>Uwagi

`IStorage` Obiekt musi istnieć, aby można było otworzyć lub utworzyć strumień, chyba że jest to strumień pamięci.

`COleStreamFile`obiekty są manipulowane dokładnie tak, jak obiekty [CFile](../../mfc/reference/cfile-class.md) .

Aby uzyskać więcej informacji na temat manipulowania strumieniami i magazynami, [Zobacz kontenery artykułów: Pliki](../../mfc/containers-compound-files.md)złożone...

Aby uzyskać więcej informacji, zobacz [IStream](/windows/win32/api/objidl/nn-objidl-istream) i [Metoda IStorage](/windows/win32/api/objidl/nn-objidl-istorage) w Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`COleStreamFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** Afxole. h

##  <a name="attach"></a>COleStreamFile:: Attach

Kojarzy dostarczony strumień OLE z `COleStreamFile` obiektem.

```
void Attach(LPSTREAM lpStream);
```

### <a name="parameters"></a>Parametry

*lpStream*<br/>
Wskazuje strumień OLE (`IStream`), który ma być skojarzony z obiektem. Nie może mieć wartości NULL.

### <a name="remarks"></a>Uwagi

Obiekt nie może już być skojarzony ze strumieniem OLE.

Aby uzyskać więcej informacji, zobacz [IStream](/windows/win32/api/objidl/nn-objidl-istream) w Windows SDK.

##  <a name="colestreamfile"></a>COleStreamFile::COleStreamFile

`COleStreamFile` Tworzy obiekt.

```
COleStreamFile(LPSTREAM lpStream = NULL);
```

### <a name="parameters"></a>Parametry

*lpStream*<br/>
Wskaźnik do strumienia OLE, który ma zostać skojarzony z obiektem.

### <a name="remarks"></a>Uwagi

Jeśli *LPSTREAM* ma wartość null, obiekt nie jest skojarzony ze strumieniem OLE, w przeciwnym razie obiekt jest skojarzony z dostarczonym strumieniem OLE.

Aby uzyskać więcej informacji, zobacz [IStream](/windows/win32/api/objidl/nn-objidl-istream) w Windows SDK.

##  <a name="creatememorystream"></a>COleStreamFile::CreateMemoryStream

Bezpiecznie tworzy nowy strumień poza globalną, udostępnioną pamięcią, w której wystąpił błąd normalny, oczekiwany warunek.

```
BOOL CreateMemoryStream(CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*pError*<br/>
Wskazuje obiekt [CFileException](../../mfc/reference/cfileexception-class.md) lub wartość null, który wskazuje na stan ukończenia operacji tworzenia. Podaj ten parametr, jeśli chcesz monitorować możliwe wyjątki wygenerowane przez próbę utworzenia strumienia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli strumień został utworzony pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pamięć jest przydzielone przez podsystem OLE.

Aby uzyskać więcej informacji, zobacz [CreateStreamOnHGlobal](/windows/win32/api/combaseapi/nf-combaseapi-createstreamonhglobal) w Windows SDK.

##  <a name="createstream"></a>COleStreamFile:: isstream

Bezpiecznie tworzy nowy strumień w podanym obiekcie magazynu, w którym wystąpił błąd normalny, oczekiwany warunek.

```
BOOL CreateStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*lpStorage*<br/>
Wskazuje obiekt magazynu OLE, który zawiera strumień, który ma zostać utworzony. Nie może mieć wartości NULL.

*lpszStreamName*<br/>
Nazwa strumienia, który ma zostać utworzony. Nie może mieć wartości NULL.

*nOpenFlags*<br/>
Tryb dostępu do użycia podczas otwierania strumienia. Domyślnie używane są tryb wyłączny, odczyt/zapis i tworzenie. Aby uzyskać pełną listę dostępnych trybów, zobacz [CFile:: CFile](../../mfc/reference/cfile-class.md#cfile).

*pError*<br/>
Wskazuje obiekt [CFileException](../../mfc/reference/cfileexception-class.md) lub wartość null. Podaj ten parametr, jeśli chcesz monitorować możliwe wyjątki wygenerowane przez próbę utworzenia strumienia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli strumień został utworzony pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wyjątek pliku zostanie wygenerowany, jeśli otwarcie nie powiedzie się, a *pError* nie ma wartości null.

Aby uzyskać więcej informacji, zobacz [Metoda IStorage:: isstream](/windows/win32/api/objidl/nf-objidl-istorage-createstream) w Windows SDK.

##  <a name="detach"></a>COleStreamFile::D etach

Usuwa strumień z obiektu bez zamykania strumienia.

```
LPSTREAM Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do strumienia (`IStream`), który został skojarzony z obiektem.

### <a name="remarks"></a>Uwagi

Strumień musi być zamknięty w inny sposób przed zakończeniem działania programu.

Aby uzyskać więcej informacji, zobacz [IStream](/windows/win32/api/objidl/nn-objidl-istream) w Windows SDK.

##  <a name="getstream"></a>COleStreamFile::GetStream

Wywołaj tę funkcję, aby zwrócić wskaźnik do bieżącego strumienia.

```
IStream* GetStream() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bieżącego interfejsu strumienia ( [IStream](/windows/win32/api/objidl/nn-objidl-istream)).

##  <a name="openstream"></a>COleStreamFile::OpenStream

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
Wskazuje obiekt magazynu OLE, który zawiera strumień, który ma zostać otwarty. Nie może mieć wartości NULL.

*lpszStreamName*<br/>
Nazwa strumienia do otwarcia. Nie może mieć wartości NULL.

*nOpenFlags*<br/>
Tryb dostępu do użycia podczas otwierania strumienia. Domyślnie są używane tryby wyłącznego i do odczytu i zapisu. Aby uzyskać pełną listę dostępnych trybów, zobacz [CFile:: CFile](../../mfc/reference/cfile-class.md#cfile).

*pError*<br/>
Wskazuje obiekt [CFileException](../../mfc/reference/cfileexception-class.md) lub wartość null. Podaj ten parametr, jeśli chcesz monitorować możliwe wyjątki wygenerowane przez próbę otwarcia strumienia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli strumień został otwarty pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wyjątek pliku zostanie wygenerowany, jeśli otwarcie nie powiedzie się, a *pError* nie ma wartości null.

Aby uzyskać więcej informacji, zobacz [Metoda IStorage:: OpenStream](/windows/win32/api/objidl/nf-objidl-istorage-openstream) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa CFile](../../mfc/reference/cfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
