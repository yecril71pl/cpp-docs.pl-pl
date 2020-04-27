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
ms.openlocfilehash: 75177c195e83a4ab3ad2a6bd4d608d07f8c2234f
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168088"
---
# <a name="catlfilemappingbase-class"></a>Klasa CAtlFileMappingBase

Ta klasa reprezentuje plik mapowany w pamięci.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```cpp
class CAtlFileMappingBase
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|Konstruktor.|
|[CAtlFileMappingBase:: ~ CAtlFileMappingBase](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|Wywołaj tę metodę, aby skopiować z obiektu mapowania plików.|
|[CAtlFileMappingBase:: GetData](#getdata)|Wywołaj tę metodę, aby pobrać dane z obiektu mapowania plików.|
|[CAtlFileMappingBase:: GetHandle](#gethandle)|Wywołaj tę metodę, aby zwrócić dojście do pliku.|
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|Wywołaj tę metodę, aby uzyskać rozmiar mapowania z obiektu mapowania plików.|
|[CAtlFileMappingBase:: MapFile](#mapfile)|Wywołaj tę metodę, aby utworzyć obiekt mapowania plików.|
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|Wywołaj tę metodę, aby utworzyć obiekt mapowania plików, który umożliwia pełny dostęp do wszystkich procesów.|
|[CAtlFileMappingBase::OpenMapping](#openmapping)|Wywołaj tę metodę, aby zwrócić uchwyt do obiektu mapowania plików.|
|[CAtlFileMappingBase:: demapowanie](#unmap)|Wywołaj tę metodę, aby usunąć mapowanie obiektu mapowania plików.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlFileMappingBase:: operator =](#operator_eq)|Ustawia bieżący obiekt mapowania plików na inny obiekt mapowania plików.|

## <a name="remarks"></a>Uwagi

Mapowanie pliku to skojarzenie zawartości pliku z częścią wirtualnej przestrzeni adresowej procesu. Ta klasa udostępnia metody tworzenia obiektów mapowania plików, które umożliwiają programom łatwe uzyskiwanie dostępu do danych i udostępnianie ich.

Aby uzyskać więcej informacji, zobacz [mapowanie plików](/windows/win32/Memory/file-mapping) w Windows SDK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlfile. h

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="catlfilemappingbase"></a>CAtlFileMappingBase::CAtlFileMappingBase

Konstruktor.

```cpp
CAtlFileMappingBase(CAtlFileMappingBase& orig);
CAtlFileMappingBase() throw();
```

### <a name="parameters"></a>Parametry

*orig*<br/>
Oryginalny obiekt mapowania plików do skopiowania w celu utworzenia nowego obiektu.

### <a name="remarks"></a>Uwagi

Tworzy nowy obiekt mapowania plików, opcjonalnie używając istniejącego obiektu. Nadal konieczne jest wywołanie [CAtlFileMappingBase:: mapfile](#mapfile) w celu otworzenia lub utworzenia obiektu mapowania plików dla określonego pliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="dtor"></a>CAtlFileMappingBase:: ~ CAtlFileMappingBase

Destruktor.

```cpp
~CAtlFileMappingBase() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie zasoby przydzielone przez klasę i wywołuje metodę [CAtlFileMappingBase:: demapowanie](#unmap) .

## <a name="catlfilemappingbasecopyfrom"></a><a name="copyfrom"></a>CAtlFileMappingBase::CopyFrom

Wywołaj tę metodę, aby skopiować z obiektu mapowania plików.

```cpp
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```

### <a name="parameters"></a>Parametry

*orig*<br/>
Oryginalny obiekt mapowania plików do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="catlfilemappingbasegetdata"></a><a name="getdata"></a>CAtlFileMappingBase:: GetData

Wywołaj tę metodę, aby pobrać dane z obiektu mapowania plików.

```cpp
void* GetData() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do danych.

## <a name="catlfilemappingbasegethandle"></a><a name="gethandle"></a>CAtlFileMappingBase:: GetHandle

Wywołaj tę metodę, aby zwrócić uchwyt do obiektu mapowania plików.

```cpp
HANDLE GetHandle() throw ();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt do obiektu mapowania plików.

## <a name="catlfilemappingbasegetmappingsize"></a><a name="getmappingsize"></a>CAtlFileMappingBase::GetMappingSize

Wywołaj tę metodę, aby uzyskać rozmiar mapowania z obiektu mapowania plików.

```cpp
SIZE_T GetMappingSize() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca rozmiar mapowania.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlFileMappingBase:: CAtlFileMappingBase](#catlfilemappingbase).

## <a name="catlfilemappingbasemapfile"></a><a name="mapfile"></a>CAtlFileMappingBase:: MapFile

Wywołaj tę metodę, aby otworzyć lub utworzyć obiekt mapowania plików dla określonego pliku.

```cpp
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```

### <a name="parameters"></a>Parametry

*hFile*<br/>
Dojście do pliku, z którego ma zostać utworzony obiekt mapowania. *hFile* musi być prawidłowy i nie może być ustawiony na INVALID_HANDLE_VALUE.

*nMappingSize*<br/>
Rozmiar mapowania. W przypadku wartości 0 maksymalny rozmiar obiektu mapowania plików jest równy bieżącemu rozmiarowi pliku identyfikowanemu przez *hFile.*

*nOffset*<br/>
Przesunięcie pliku, w którym ma zostać rozpoczęte mapowanie. Wartość przesunięcia musi być wielokrotnością stopnia szczegółowości alokacji pamięci systemu.

*dwMappingProtection*<br/>
Ochrona wymagana dla widoku pliku, gdy plik jest zamapowany. Zobacz *flProtect* in [funkcja CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) w Windows SDK.

*dwViewDesiredAccess*<br/>
Określa typ dostępu do widoku pliku, w związku z czym ochrona stron mapowanych przez plik. Zobacz *dwDesiredAccess* in [Funkcja MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Po utworzeniu obiektu mapowania plików, rozmiar pliku nie może przekraczać rozmiaru obiektu mapowania plików; Jeśli tak nie jest, nie wszystkie zawartości plików będą dostępne do udostępnienia. Aby uzyskać więcej informacji, zobacz [funkcja CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) i [Funkcja MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) w Windows SDK.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlFileMappingBase:: CAtlFileMappingBase](#catlfilemappingbase).

## <a name="catlfilemappingbasemapsharedmem"></a><a name="mapsharedmem"></a>CAtlFileMappingBase::MapSharedMem

Wywołaj tę metodę, aby utworzyć obiekt mapowania plików, który umożliwia pełny dostęp do wszystkich procesów.

```cpp
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
Rozmiar mapowania. W przypadku wartości 0 maksymalny rozmiar obiektu mapowania plików jest równy bieżącemu rozmiarowi obiektu mapowania plików identyfikowanego przez *szName*.

*szName*<br/>
Nazwa obiektu mapowania.

*pbAlreadyExisted*<br/>
Wskazuje wartość logiczną, która jest ustawiona na wartość TRUE, jeśli obiekt mapowania już istnieje.

*lpsa*<br/>
Wskaźnik do `SECURITY_ATTRIBUTES` struktury, który określa, czy zwracany uchwyt może być dziedziczony przez procesy podrzędne. Zobacz *lpAttributes* in [funkcja CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) w Windows SDK.

*dwMappingProtection*<br/>
Ochrona wymagana dla widoku pliku, gdy plik jest zamapowany. Zobacz *flProtect* w `CreateFileMapping` programie w Windows SDK.

*dwViewDesiredAccess*<br/>
Określa typ dostępu do widoku pliku, w związku z czym ochrona stron mapowanych przez plik. Zobacz *dwDesiredAccess* in [Funkcja MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

`MapShareMem`zezwala na współużytkowanie istniejącego obiektu mapowania plików utworzonego przez [funkcja CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga)w celu współdzielenia między procesami.

## <a name="catlfilemappingbaseopenmapping"></a><a name="openmapping"></a>CAtlFileMappingBase::OpenMapping

Wywołaj tę metodę, aby otworzyć nazwany obiekt mapowania plików dla określonego pliku.

```cpp
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>Parametry

*szName*<br/>
Nazwa obiektu mapowania. Jeśli istnieje otwarte dojście do obiektu mapowania plików o tej nazwie, a deskryptor zabezpieczeń obiektu mapowania nie powoduje konfliktu z parametrem *dwViewDesiredAccess* , operacja otwarcia zostanie zakończona pomyślnie.

*nMappingSize*<br/>
Rozmiar mapowania. W przypadku wartości 0 maksymalny rozmiar obiektu mapowania plików jest równy bieżącemu rozmiarowi obiektu mapowania plików identyfikowanego przez *szName*.

*nOffset*<br/>
Przesunięcie pliku, w którym ma zostać rozpoczęte mapowanie. Wartość przesunięcia musi być wielokrotnością stopnia szczegółowości alokacji pamięci systemu.

*dwViewDesiredAccess*<br/>
Określa typ dostępu do widoku pliku, w związku z czym ochrona stron mapowanych przez plik. Zobacz *dwDesiredAccess* in [Funkcja MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli parametry wejściowe są nieprawidłowe.

## <a name="catlfilemappingbaseoperator-"></a><a name="operator_eq"></a>CAtlFileMappingBase:: operator =

Ustawia bieżący obiekt mapowania plików na inny obiekt mapowania plików.

```cpp
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```

### <a name="parameters"></a>Parametry

*orig*<br/>
Bieżący obiekt mapowania plików.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do bieżącego obiektu.

## <a name="catlfilemappingbaseunmap"></a><a name="unmap"></a>CAtlFileMappingBase:: demapowanie

Wywołaj tę metodę, aby usunąć mapowanie obiektu mapowania plików.

```cpp
HRESULT Unmap() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Funkcja UnmapViewOfFile](/windows/win32/api/memoryapi/nf-memoryapi-unmapviewoffile) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
