---
title: Klasa CMonikerFile
ms.date: 11/04/2016
f1_keywords:
- CMonikerFile
- AFXOLE/CMonikerFile
- AFXOLE/CMonikerFile::CMonikerFile
- AFXOLE/CMonikerFile::Close
- AFXOLE/CMonikerFile::Detach
- AFXOLE/CMonikerFile::GetMoniker
- AFXOLE/CMonikerFile::Open
- AFXOLE/CMonikerFile::CreateBindContext
helpviewer_keywords:
- CMonikerFile [MFC], CMonikerFile
- CMonikerFile [MFC], Close
- CMonikerFile [MFC], Detach
- CMonikerFile [MFC], GetMoniker
- CMonikerFile [MFC], Open
- CMonikerFile [MFC], CreateBindContext
ms.assetid: 87be5966-f4f7-4235-bce2-1fa39e9417de
ms.openlocfilehash: 56283b56a1c0832d34ce23c7db47c47d9480aec8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504565"
---
# <a name="cmonikerfile-class"></a>Klasa CMonikerFile

Reprezentuje strumień danych ( [IStream](/windows/win32/api/objidl/nn-objidl-istream)) o nazwie [IMoniker —](/windows/win32/api/objidl/nn-objidl-imoniker).

## <a name="syntax"></a>Składnia

```
class CMonikerFile : public COleStreamFile
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMonikerFile::CMonikerFile](#cmonikerfile)|Konstruuje `CMonikerFile` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMonikerFile::Close](#close)|Odłącza i zwalnia strumień oraz zwalnia moniker.|
|[CMonikerFile::Detach](#detach)|Odłącza `CMonikerFile` od tego obiektu. `IMoniker`|
|[CMonikerFile::GetMoniker](#getmoniker)|Zwraca bieżący moniker.|
|[CMonikerFile:: Open](#open)|Otwiera określony plik w celu uzyskania strumienia.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMonikerFile::CreateBindContext](#createbindcontext)|Uzyskuje kontekst powiązania lub tworzy domyślny kontekst powiązania zainicjowany.|

## <a name="remarks"></a>Uwagi

Moniker zawiera informacje podobne do nazwy ścieżki do pliku. Jeśli masz wskaźnik do `IMoniker` interfejsu obiektu monikera, możesz uzyskać dostęp do określonego pliku bez jakichkolwiek innych szczegółowych informacji o tym, gdzie znajduje się plik.

Pochodny `COleStreamFile`od `CMonikerFile` , przyjmuje moniker lub reprezentację ciągu, może zostać przekształcony w moniker i powiązać ze strumieniem, dla którego moniker jest nazwą. Następnie możesz odczytywać i zapisywać dane w tym strumieniu. Celem `CMonikerFile` jest zapewnienie prostego dostępu do `IStream`s o nazwie `IMoniker`do, aby nie trzeba było samodzielnie powiązać ze strumieniem, ale mieć `CFile` funkcjonalność strumienia.

`CMonikerFile`nie można użyć do powiązania ze wszystkimi elementami poza strumieniem. Jeśli chcesz powiązać z magazynem lub obiektem, musisz użyć `IMoniker` interfejsu bezpośrednio.

Aby uzyskać więcej informacji na temat strumieni i monikerów, zobacz [COleStreamFile](../../mfc/reference/colestreamfile-class.md) w *dokumentacji MFC* i [IStream](/windows/win32/api/objidl/nn-objidl-istream) i [IMoniker —](/windows/win32/api/objidl/nn-objidl-imoniker) w Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

`CMonikerFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** Afxole. h

##  <a name="close"></a>CMonikerFile:: Close

Wywołaj tę funkcję w celu odłączenia i zwolnienia strumienia i zwolnienia monikera.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Może być wywoływana dla nieotwartych lub już zamkniętych strumieni.

##  <a name="cmonikerfile"></a>CMonikerFile::CMonikerFile

Konstruuje `CMonikerFile` obiekt.

```
CMonikerFile();
```

##  <a name="createbindcontext"></a>CMonikerFile::CreateBindContext

Wywołaj tę funkcję, aby utworzyć domyślny kontekst powiązania zainicjowany.

```
IBindCtx* CreateBindContext(CFileException* pError);
```

### <a name="parameters"></a>Parametry

*pError*<br/>
Wskaźnik do wyjątku pliku. W przypadku błędu zostanie ona ustawiona na przyczynę.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik prowadzący do powiązania [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) , z którym zostanie wykonane pomyślne; w przeciwnym razie wartość NULL. Jeśli wystąpienie zostało otwarte przy użyciu `IBindHost` interfejsu, kontekst powiązania jest pobierany `IBindHost`z. Jeśli nie `IBindHost` ma interfejsu lub interfejs nie zwróci kontekstu powiązania, zostanie utworzony kontekst powiązania. Opis interfejsu [IBindHost](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775076\(v=vs.85\)) można znaleźć w Windows SDK.

### <a name="remarks"></a>Uwagi

Kontekst powiązania to obiekt, który przechowuje informacje o określonej operacji powiązania monikera. Można zastąpić tę funkcję, aby zapewnić niestandardowy kontekst powiązania.

##  <a name="detach"></a>CMonikerFile::D etach

Wywołaj tę funkcję, aby zamknąć strumień.

```
BOOL Detach(CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*pError*<br/>
Wskaźnik do wyjątku pliku. W przypadku błędu zostanie ona ustawiona na przyczynę.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

##  <a name="getmoniker"></a>CMonikerFile:: GetMoniker

Wywołaj tę funkcję, aby pobrać wskaźnik do bieżącego monikera.

```
IMoniker* GetMoniker() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bieżącego interfejsu monikera ( [IMoniker —](/windows/win32/api/objidl/nn-objidl-imoniker)).

### <a name="remarks"></a>Uwagi

Ponieważ `CMonikerFile` nie jest interfejsem, zwrócony wskaźnik nie zwiększa liczby odwołań (do [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)), a moniker `CMonikerFile` jest uwalniany po wydaniu obiektu. Jeśli chcesz, aby w monikerze lub samodzielnie ją wypróbować, `AddRef` musisz ją.

##  <a name="open"></a>CMonikerFile:: Open

Wywołaj tę funkcję elementu członkowskiego, aby otworzyć plik lub obiekt monikera.

```
virtual BOOL Open(
    LPCTSTR lpszURL,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*lpszURL*<br/>
Adres URL lub nazwa pliku, który ma zostać otwarty.

*pError*<br/>
Wskaźnik do wyjątku pliku. W przypadku błędu zostanie ona ustawiona na przyczynę.

*pMoniker*<br/>
Wskaźnik do interfejsu `IMoniker` monikera, który ma zostać użyty w celu uzyskania strumienia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Nie można użyć parametru *lpszURL* na komputerze Mac. Tylko `Open` forma *pMoniker* może być używana w przypadku komputerów Macintosh.

Możesz użyć adresu URL lub nazwy pliku dla parametru *lpszURL* . Przykład:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]

\- lub —

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]

## <a name="see-also"></a>Zobacz także

[Klasa COleStreamFile](../../mfc/reference/colestreamfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)
