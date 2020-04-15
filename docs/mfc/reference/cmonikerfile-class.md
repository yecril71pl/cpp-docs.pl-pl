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
ms.openlocfilehash: fc74ad2499fcde63faa2c5859a87fd9ffd2846eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319773"
---
# <a name="cmonikerfile-class"></a>Klasa CMonikerFile

Reprezentuje strumień danych [(IStream)](/windows/win32/api/objidl/nn-objidl-istream)nazwany przez [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker).

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
|[CMonikerFile::Zamknij](#close)|Odłącza i zwalnia strumień i zwalnia moniker.|
|[CMonikerFile::Detach](#detach)|Odłącza `IMoniker` od `CMonikerFile` tego obiektu.|
|[CMonikerFile::GetMoniker](#getmoniker)|Zwraca bieżącą moniker.|
|[CMonikerFile::Otwórz](#open)|Otwiera określony plik, aby uzyskać strumień.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[Plik CMoniker::CreateBindContext](#createbindcontext)|Uzyskuje kontekst powiązania lub tworzy domyślny kontekst zainicjowane powiązania.|

## <a name="remarks"></a>Uwagi

Moniker zawiera informacje podobne do nazwy ścieżki do pliku. Jeśli masz wskaźnik do `IMoniker` interfejsu obiektu monikera, możesz uzyskać dostęp do zidentyfikowanego pliku bez żadnych innych szczegółowych informacji o tym, gdzie plik faktycznie się znajduje.

Pochodna `COleStreamFile`z `CMonikerFile` , przyjmuje moniker lub reprezentacji ciąg może dokonać w monikera i wiąże się ze strumieniem, dla którego moniker jest nazwą. Następnie można odczytać i zapisać do tego strumienia. Prawdziwym celem `CMonikerFile` jest zapewnienie prostego `IStream`dostępu `IMoniker`do s nazwany przez s, tak aby nie `CFile` trzeba powiązać ze strumieniem siebie, ale mają funkcje do strumienia.

`CMonikerFile`nie może być używany do powiązania z niczym innym niż strumień. Jeśli chcesz powiązać z magazynem lub obiektem, należy użyć `IMoniker` interfejsu bezpośrednio.

Aby uzyskać więcej informacji na temat strumieni i monikerów, zobacz [COleStreamFile](../../mfc/reference/colestreamfile-class.md) w *odwołaniu MFC* i [IStream](/windows/win32/api/objidl/nn-objidl-istream) i [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) w windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cfile](../../mfc/reference/cfile-class.md)

[Colestreamfile](../../mfc/reference/colestreamfile-class.md)

`CMonikerFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

## <a name="cmonikerfileclose"></a><a name="close"></a>CMonikerFile::Zamknij

Wywołanie tej funkcji, aby odłączyć i zwolnić strumień i zwolnić moniker.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Można wywołać na nieotwartych lub już zamkniętych strumieni.

## <a name="cmonikerfilecmonikerfile"></a><a name="cmonikerfile"></a>CMonikerFile::CMonikerFile

Konstruuje `CMonikerFile` obiekt.

```
CMonikerFile();
```

## <a name="cmonikerfilecreatebindcontext"></a><a name="createbindcontext"></a>Plik CMoniker::CreateBindContext

Wywołanie tej funkcji, aby utworzyć domyślny kontekst zainicjowane powiązania.

```
IBindCtx* CreateBindContext(CFileException* pError);
```

### <a name="parameters"></a>Parametry

*Perror*<br/>
Wskaźnik do wyjątku pliku. W przypadku wystąpienia błędu zostanie on ustawiony na przyczynę.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do kontekstu powiązania [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) do powiązania z jeśli zakończy się pomyślnie; w przeciwnym razie NULL. Jeśli wystąpienie zostało `IBindHost` otwarte za pomocą interfejsu, kontekst `IBindHost`powiązania jest pobierany z . Jeśli nie `IBindHost` ma interfejsu lub interfejs nie może zwrócić kontekst powiązania, tworzony jest kontekst powiązania. Opis interfejsu [IBindHost można znaleźć](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775076\(v=vs.85\)) w zestaw Windows SDK.

### <a name="remarks"></a>Uwagi

Kontekst powiązania jest obiektem, który przechowuje informacje o określonej operacji wiązania moniker. Tę funkcję można zastąpić, aby zapewnić niestandardowy kontekst powiązania.

## <a name="cmonikerfiledetach"></a><a name="detach"></a>CMonikerFile::Detach

Wywołanie tej funkcji, aby zamknąć strumień.

```
BOOL Detach(CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*Perror*<br/>
Wskaźnik do wyjątku pliku. W przypadku wystąpienia błędu zostanie on ustawiony na przyczynę.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

## <a name="cmonikerfilegetmoniker"></a><a name="getmoniker"></a>CMonikerFile::GetMoniker

Wywołanie tej funkcji, aby pobrać wskaźnik do bieżącego moniker.

```
IMoniker* GetMoniker() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bieżącego interfejsu moniker ( [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)).

### <a name="remarks"></a>Uwagi

Ponieważ `CMonikerFile` nie jest interfejsem, wskaźnik zwracany nie zwiększa liczby odwołań (za pośrednictwem [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)), a moniker jest zwalniany po zwolnieniu `CMonikerFile` obiektu. Jeśli chcesz trzymać się pseudonimu lub zwolnić go `AddRef` samodzielnie, musisz go.

## <a name="cmonikerfileopen"></a><a name="open"></a>CMonikerFile::Otwórz

Wywołanie tej funkcji elementu członkowskiego, aby otworzyć plik lub obiekt moniker.

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

*Perror*<br/>
Wskaźnik do wyjątku pliku. W przypadku wystąpienia błędu zostanie on ustawiony na przyczynę.

*pMoniker (własnik pmoniker)*<br/>
Wskaźnik do interfejsu monikera, `IMoniker` który ma być używany do uzyskania strumienia.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Parametru *lpszURL* nie można używać na komputerze Macintosh. Tylko *forma pMoniker* `Open` może być używana na komputerze Macintosh.

Można użyć adresu URL lub nazwy pliku dla parametru *lpszURL.* Przykład:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]

\-lub -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa COleStreamFile](../../mfc/reference/colestreamfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)
