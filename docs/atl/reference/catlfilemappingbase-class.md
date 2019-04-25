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
ms.openlocfilehash: d31bc72e485fbb15ed595a7c777c3685a00865c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260347"
---
# <a name="catlfilemappingbase-class"></a>Klasa CAtlFileMappingBase

Ta klasa reprezentuje plik mapowanych na pamięć.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

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
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|Wywołaj tę metodę, aby skopiować z obiektu mapowania pliku.|
|[CAtlFileMappingBase::GetData](#getdata)|Wywołaj tę metodę, aby uzyskać dane z obiektu mapowania pliku.|
|[CAtlFileMappingBase::GetHandle](#gethandle)|Wywołaj tę metodę, aby zwrócić dojście do pliku.|
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|Wywołaj tę metodę, aby uzyskać rozmiar mapowania z obiektu mapowania pliku.|
|[CAtlFileMappingBase::MapFile](#mapfile)|Wywołaj tę metodę można utworzyć obiektu mapowania pliku.|
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|Wywołaj tę metodę można utworzyć obiektu mapowania pliku, który zezwala na pełny dostęp do wszystkich procesów.|
|[CAtlFileMappingBase::OpenMapping](#openmapping)|Wywołaj tę metodę, aby zwrócić dojścia do obiektu mapowania pliku.|
|[CAtlFileMappingBase::Unmap](#unmap)|Wywołaj tę metodę w celu mapowania obiektu mapowania pliku.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlFileMappingBase::operator =](#operator_eq)|Ustawia bieżący obiekt mapowanie pliku do innego obiektu mapowania pliku.|

## <a name="remarks"></a>Uwagi

Mapowanie pliku jest skojarzenie zawartość pliku z części wirtualnej przestrzeni adresowej procesu. Ta klasa dostarcza metody do tworzenia obiektów w pliku mapowania, zezwalające na programy, aby łatwo uzyskiwać dostęp do i udostępniania danych.

Aby uzyskać więcej informacji, zobacz [mapowania pliku](/windows/desktop/Memory/file-mapping) w zestawie Windows SDK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlfile.h

##  <a name="catlfilemappingbase"></a>  CAtlFileMappingBase::CAtlFileMappingBase

Konstruktor.

```
CAtlFileMappingBase(CAtlFileMappingBase& orig);
CAtlFileMappingBase() throw();
```

### <a name="parameters"></a>Parametry

*ORIG*<br/>
Oryginalnego obiektu mapowania pliku do skopiowania można utworzyć nowego obiektu.

### <a name="remarks"></a>Uwagi

Tworzy nowy obiekt pliku mapowania, opcjonalnie używając istniejącego obiektu. Nadal jest wymagane do wywołania [CAtlFileMappingBase::MapFile](#mapfile) próbę otwarcia lub utworzenia obiektu mapowania pliku dla danego pliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]

##  <a name="dtor"></a>  CAtlFileMappingBase:: ~ CAtlFileMappingBase

Destruktor.

```
~CAtlFileMappingBase() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie zasoby przydzielone przez klasy i wywołania [CAtlFileMappingBase::Unmap](#unmap) metody.

##  <a name="copyfrom"></a>  CAtlFileMappingBase::CopyFrom

Wywołaj tę metodę, aby skopiować z obiektu mapowania pliku.

```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```

### <a name="parameters"></a>Parametry

*ORIG*<br/>
Oryginalnego obiektu mapowania pliku do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="getdata"></a>  CAtlFileMappingBase::GetData

Wywołaj tę metodę, aby uzyskać dane z obiektu mapowania pliku.

```
void* GetData() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do danych.

##  <a name="gethandle"></a>  CAtlFileMappingBase::GetHandle

Wywołaj tę metodę, aby zwrócić dojścia do obiektu mapowania pliku.

```
HANDLE GetHandle() throw ();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt do obiektu mapowania pliku.

##  <a name="getmappingsize"></a>  CAtlFileMappingBase::GetMappingSize

Wywołaj tę metodę, aby uzyskać rozmiar mapowania z obiektu mapowania pliku.

```
SIZE_T GetMappingSize() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca rozmiar mapowania.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).

##  <a name="mapfile"></a>  CAtlFileMappingBase::MapFile

Wywołaj tę metodę w celu otwarcia lub utworzenia obiektu mapowania pliku dla określonego pliku.

```
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```

### <a name="parameters"></a>Parametry

*hFile*<br/>
Dojście do pliku, z którego można utworzyć obiektu mapowania. *hFile* musi być prawidłowy i nie można ustawić INVALID_HANDLE_VALUE.

*nMappingSize*<br/>
Rozmiar mapowania. Jeśli jest to 0, maksymalny rozmiar obiektu mapowania pliku jest równy rozmiarowi bieżącemu pliku identyfikowane przez *hFile.*

*nOffset*<br/>
Przesunięcie w pliku, gdy mapowanie jest rozpoczęcie. Wartość przesunięcia musi być wielokrotnością stopnia szczegółowości alokacji pamięci systemu.

*dwMappingProtection*<br/>
Ochrona żądanego widoku pliku, gdy plik jest zamapowany. Zobacz *flProtect* w [funkcja CreateFileMapping](/windows/desktop/api/winbase/nf-winbase-createfilemappinga) w zestawie Windows SDK.

*dwViewDesiredAccess*<br/>
Określa typ dostępu do widoku pliku, a więc ochrony stron zamapowane przy użyciu pliku. Zobacz *dwDesiredAccess* w [funkcja MapViewOfFileEx](/windows/desktop/api/memoryapi/nf-memoryapi-mapviewoffileex) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Po utworzeniu obiektu mapowania pliku, rozmiar pliku nie może przekraczać rozmiaru obiektu mapowania pliku. Jeśli tak jest, nie wszystkie jego zawartość będzie dostępne na potrzeby udostępniania. Aby uzyskać więcej informacji, zobacz [funkcja CreateFileMapping](/windows/desktop/api/winbase/nf-winbase-createfilemappinga) i [funkcja MapViewOfFileEx](/windows/desktop/api/memoryapi/nf-memoryapi-mapviewoffileex) w zestawie Windows SDK.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).

##  <a name="mapsharedmem"></a>  CAtlFileMappingBase::MapSharedMem

Wywołaj tę metodę można utworzyć obiektu mapowania pliku, który zezwala na pełny dostęp do wszystkich procesów.

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
Rozmiar mapowania. Jeśli jest to 0, maksymalny rozmiar obiektu mapowania pliku jest równy rozmiarowi bieżącemu identyfikowane za pomocą obiektu mapowania pliku *szName*.

*szName*<br/>
Nazwa obiektu mapowania.

*pbAlreadyExisted*<br/>
Wskazuje wartość logiczna, która jest ustawiona na wartość TRUE, jeśli mapowanie obiektu już istnieje.

*lpsa*<br/>
Wskaźnik do `SECURITY_ATTRIBUTES` strukturę, która określa, czy zwracany uchwyt może być dziedziczony przez procesy podrzędne. Zobacz *lpAttributes* w [funkcja CreateFileMapping](/windows/desktop/api/winbase/nf-winbase-createfilemappinga) w zestawie Windows SDK.

*dwMappingProtection*<br/>
Ochrona żądanego widoku pliku, gdy plik jest zamapowany. Zobacz *flProtect* w `CreateFileMapping` w zestawie Windows SDK.

*dwViewDesiredAccess*<br/>
Określa typ dostępu do widoku pliku, a więc ochrony stron zamapowane przy użyciu pliku. Zobacz *dwDesiredAccess* w [funkcja MapViewOfFileEx](/windows/desktop/api/memoryapi/nf-memoryapi-mapviewoffileex) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

`MapShareMem` Umożliwia istniejącego obiektu mapowania pliku, utworzone przez [funkcja CreateFileMapping](/windows/desktop/api/winbase/nf-winbase-createfilemappinga), aby współdzielić je między procesami.

##  <a name="openmapping"></a>  CAtlFileMappingBase::OpenMapping

Wywołaj tę metodę, aby otworzyć nazwanego obiektu mapowania pliku dla określonego pliku.

```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>Parametry

*szName*<br/>
Nazwa obiektu mapowania. Jeśli jest otwarte dojście do obiektu mapowania pliku przy użyciu tej nazwy, a deskryptora zabezpieczeń obiektu mapowania nie powoduje konfliktu z *dwViewDesiredAccess* parametru, operacja otwierania zakończy się pomyślnie.

*nMappingSize*<br/>
Rozmiar mapowania. Jeśli jest to 0, maksymalny rozmiar obiektu mapowania pliku jest równy rozmiarowi bieżącemu identyfikowane za pomocą obiektu mapowania pliku *szName*.

*nOffset*<br/>
Przesunięcie w pliku, gdy mapowanie jest rozpoczęcie. Wartość przesunięcia musi być wielokrotnością stopnia szczegółowości alokacji pamięci systemu.

*dwViewDesiredAccess*<br/>
Określa typ dostępu do widoku pliku, a więc ochrony stron zamapowane przy użyciu pliku. Zobacz *dwDesiredAccess* w [funkcja MapViewOfFileEx](/windows/desktop/api/memoryapi/nf-memoryapi-mapviewoffileex) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli parametry wejściowe są nieprawidłowe.

##  <a name="operator_eq"></a>  CAtlFileMappingBase::operator =

Ustawia bieżący obiekt mapowanie pliku do innego obiektu mapowania pliku.

```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```

### <a name="parameters"></a>Parametry

*ORIG*<br/>
Bieżący obiekt pliku mapowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do bieżącego obiektu.

##  <a name="unmap"></a>  CAtlFileMappingBase::Unmap

Wywołaj tę metodę w celu mapowania obiektu mapowania pliku.

```
HRESULT Unmap() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Zobacz [UnmapViewOfFile](/windows/desktop/api/memoryapi/nf-memoryapi-unmapviewoffile) w zestawie Windows SDK, aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

[Klasa CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
