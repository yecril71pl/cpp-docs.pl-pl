---
title: Klasa CAtlFileMappingBase
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CopyFrom
- ATLFILE/ATL::CAtlFileMappingBase::GetData
- ATLFILE/ATL::CAtlFileMappingBase::GetHandle
- ATLFILE/ATL::CAtlFileMappingBase::GetMappingSize
- ATLFILE/ATL::CAtlFileMappingBase::MapFile
- ATLFILE/ATL::CAtlFileMappingBase::MapSharedMem
- ATLFILE/ATL::CAtlFileMappingBase::OpenMapping
- ATLFILE/ATL::CAtlFileMappingBase::Unmap
helpviewer_keywords:
- CAtlFileMappingBase class
ms.assetid: be555723-2790-4f57-a8fb-be4d68460775
ms.openlocfilehash: ae790cf1248c78ff9aa70c0e586f86af6c8f3b9a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318943"
---
# <a name="catlfilemappingbase-class"></a>Klasa CAtlFileMappingBase

Ta klasa reprezentuje plik mapowany w pamięci.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CAtlFileMappingBase
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|Konstruktor.|
|[CAtlFileMappingBase::~CAtlFileMappingBase](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|Wywołanie tej metody, aby skopiować z obiektu mapowania plików.|
|[CAtlFileMappingBase::GetData](#getdata)|Wywołanie tej metody, aby uzyskać dane z obiektu mapowania plików.|
|[CAtlFileMappingBase::GetHandle](#gethandle)|Wywołanie tej metody, aby zwrócić dojście do pliku.|
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|Wywołanie tej metody, aby uzyskać rozmiar mapowania z obiektu mapowania plików.|
|[CAtlFileMappingBase::MapFile](#mapfile)|Wywołanie tej metody, aby utworzyć obiekt mapowania plików.|
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|Wywołanie tej metody, aby utworzyć obiekt mapowania plików, który umożliwia pełny dostęp do wszystkich procesów.|
|[CAtlFileMappingBase::OpenMapping](#openmapping)|Wywołanie tej metody, aby zwrócić dojście do obiektu mapowania plików.|
|[CAtlFileMappingBase::Unmap](#unmap)|Wywołanie tej metody, aby odmapować obiekt mapowania plików.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlFileMappingBase::operator =](#operator_eq)|Ustawia bieżący obiekt mapowania plików na inny obiekt mapowania plików.|

## <a name="remarks"></a>Uwagi

Mapowanie plików to skojarzenie zawartości pliku z częścią wirtualnej przestrzeni adresowej procesu. Ta klasa udostępnia metody tworzenia obiektów mapowania plików, które umożliwiają programom łatwy dostęp do danych i udostępnianie ich.

Aby uzyskać więcej informacji, zobacz [Mapowanie plików](/windows/win32/Memory/file-mapping) w zestawie Windows SDK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlfile.h

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="catlfilemappingbase"></a>CAtlFileMappingBase::CAtlFileMappingBase

Konstruktor.

```
CAtlFileMappingBase(CAtlFileMappingBase& orig);
CAtlFileMappingBase() throw();
```

### <a name="parameters"></a>Parametry

*Orig*<br/>
Oryginalny obiekt mapowania plików do skopiowania w celu utworzenia nowego obiektu.

### <a name="remarks"></a>Uwagi

Tworzy nowy obiekt mapowania plików, opcjonalnie przy użyciu istniejącego obiektu. Nadal konieczne jest [wywołanie CAtlFileMappingBase::MapFile,](#mapfile) aby otworzyć lub utworzyć obiekt mapowania plików dla określonego pliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="dtor"></a>CAtlFileMappingBase::~CAtlFileMappingBase

Destruktor.

```
~CAtlFileMappingBase() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie zasoby przydzielone przez klasę i wywołuje [CAtlFileMappingBase::Unmap](#unmap) metody.

## <a name="catlfilemappingbasecopyfrom"></a><a name="copyfrom"></a>CAtlFileMappingBase::CopyFrom

Wywołanie tej metody, aby skopiować z obiektu mapowania plików.

```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```

### <a name="parameters"></a>Parametry

*Orig*<br/>
Oryginalny obiekt mapowania plików do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="catlfilemappingbasegetdata"></a><a name="getdata"></a>CAtlFileMappingBase::GetData

Wywołanie tej metody, aby uzyskać dane z obiektu mapowania plików.

```
void* GetData() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do danych.

## <a name="catlfilemappingbasegethandle"></a><a name="gethandle"></a>CAtlFileMappingBase::GetHandle

Wywołanie tej metody, aby zwrócić dojście do obiektu mapowania plików.

```
HANDLE GetHandle() throw ();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca dojście do obiektu mapowania plików.

## <a name="catlfilemappingbasegetmappingsize"></a><a name="getmappingsize"></a>CAtlFileMappingBase::GetMappingSize

Wywołanie tej metody, aby uzyskać rozmiar mapowania z obiektu mapowania plików.

```
SIZE_T GetMappingSize() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca rozmiar mapowania.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).

## <a name="catlfilemappingbasemapfile"></a><a name="mapfile"></a>CAtlFileMappingBase::MapFile

Wywołanie tej metody, aby otworzyć lub utworzyć obiekt mapowania plików dla określonego pliku.

```
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```

### <a name="parameters"></a>Parametry

*hFile (plik)*<br/>
Dojście do pliku, z którego ma być utworzony obiekt mapowania. h Plik musi być *prawidłowy* i nie można go ustawić na INVALID_HANDLE_VALUE.

*nMappingSize*<br/>
Rozmiar mapowania. Jeśli 0, maksymalny rozmiar obiektu mapowania plików jest równy bieżącemu rozmiarowi pliku identyfikowanego przez *hFile.*

*nStawa*<br/>
Przesunięcie pliku, gdzie ma się rozpocząć mapowanie. Wartość przesunięcia musi być wielokrotnością szczegółowości alokacji pamięci systemu.

*dwMappingProtection*<br/>
Ochrona żądana dla widoku pliku, gdy plik jest mapowany. Zobacz *flProtect* w [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) w windows SDK.

*dwViewDesiredAccess*<br/>
Określa typ dostępu do widoku pliku, a tym samym ochronę stron mapowanych przez plik. Zobacz *dwDesiredAccess* w [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) w windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Po utworzeniu obiektu mapowania plików rozmiar pliku nie może przekraczać rozmiaru obiektu mapowania plików; Jeśli tak, nie cała zawartość pliku będzie dostępna do udostępnienia. Aby uzyskać więcej informacji, zobacz [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) i [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) w windows SDK.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).

## <a name="catlfilemappingbasemapsharedmem"></a><a name="mapsharedmem"></a>CAtlFileMappingBase::MapSharedMem

Wywołanie tej metody, aby utworzyć obiekt mapowania plików, który umożliwia pełny dostęp do wszystkich procesów.

```
HRESULT MapSharedMem(
    SIZE_T nMappingSize,
    LPCTSTR szName,
    BOOL* pbAlreadyExisted = NULL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    DWORD dwMappingProtection = PAGE_READWRITE,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>Parametry

*nMappingSize*<br/>
Rozmiar mapowania. Jeśli 0, maksymalny rozmiar obiektu mapowania plików jest równy bieżącemu rozmiarowi obiektu mapowania plików identyfikowanego przez *szName*.

*Szname*<br/>
Nazwa obiektu mapowania.

*pbAlreadyIstyed*<br/>
Wskazuje wartość BOOL ustawioną na WARTOŚĆ TRUE, jeśli obiekt mapowania już istniał.

*lpsa*<br/>
Wskaźnik do `SECURITY_ATTRIBUTES` struktury, która określa, czy zwracany uchwyt może być dziedziczona przez procesy podrzędne. Zobacz *lpAttributes* w [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) w windows SDK.

*dwMappingProtection*<br/>
Ochrona żądana dla widoku pliku, gdy plik jest mapowany. Zobacz *flProtect* w `CreateFileMapping` windows SDK.

*dwViewDesiredAccess*<br/>
Określa typ dostępu do widoku pliku, a tym samym ochronę stron mapowanych przez plik. Zobacz *dwDesiredAccess* w [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) w windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

`MapShareMem`umożliwia współużytkowanie istniejącego obiektu mapowania plików utworzonego przez [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga)między procesami.

## <a name="catlfilemappingbaseopenmapping"></a><a name="openmapping"></a>CAtlFileMappingBase::OpenMapping

Wywołanie tej metody, aby otworzyć obiekt mapowania pliku o nazwie dla określonego pliku.

```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>Parametry

*Szname*<br/>
Nazwa obiektu mapowania. Jeśli istnieje otwarty dojście do obiektu mapowania plików o tej nazwie, a deskryptor zabezpieczeń na obiekcie mapowania nie powoduje konfliktu z parametrem *dwViewDesiredAccess,* operacja otwarcia zakończy się pomyślnie.

*nMappingSize*<br/>
Rozmiar mapowania. Jeśli 0, maksymalny rozmiar obiektu mapowania plików jest równy bieżącemu rozmiarowi obiektu mapowania plików identyfikowanego przez *szName*.

*nStawa*<br/>
Przesunięcie pliku, gdzie ma się rozpocząć mapowanie. Wartość przesunięcia musi być wielokrotnością szczegółowości alokacji pamięci systemu.

*dwViewDesiredAccess*<br/>
Określa typ dostępu do widoku pliku, a tym samym ochronę stron mapowanych przez plik. Zobacz *dwDesiredAccess* w [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) w windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli parametry wejściowe są nieprawidłowe.

## <a name="catlfilemappingbaseoperator-"></a><a name="operator_eq"></a>CAtlFileMappingBase::operator =

Ustawia bieżący obiekt mapowania plików na inny obiekt mapowania plików.

```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```

### <a name="parameters"></a>Parametry

*Orig*<br/>
Bieżący obiekt mapowania plików.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do bieżącego obiektu.

## <a name="catlfilemappingbaseunmap"></a><a name="unmap"></a>CAtlFileMappingBase::Unmap

Wywołanie tej metody, aby odmapować obiekt mapowania plików.

```
HRESULT Unmap() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [UnmapViewOfFile](/windows/win32/api/memoryapi/nf-memoryapi-unmapviewoffile) w usłudze Windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
