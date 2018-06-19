---
title: Klasa CAtlFileMappingBase | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlFileMappingBase class
ms.assetid: be555723-2790-4f57-a8fb-be4d68460775
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e315a29f72c887b5bff2e8177e7a47aed18c3fd4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364447"
---
# <a name="catlfilemappingbase-class"></a>Klasa CAtlFileMappingBase
Ta klasa reprezentuje plik mapowanych na pamięć.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
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
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|Wywołaj tę metodę, aby skopiować z obiektu mapowania pliku.|  
|[CAtlFileMappingBase::GetData](#getdata)|Wywołaj tę metodę w celu pobrania danych z obiektu mapowania pliku.|  
|[CAtlFileMappingBase::GetHandle](#gethandle)|Wywołaj tę metodę, aby zwrócić dojście do pliku.|  
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|Wywołanie tej metody można pobrać rozmiaru mapowania z obiektu mapowania pliku.|  
|[CAtlFileMappingBase::MapFile](#mapfile)|Wywołanie tej metody można utworzyć obiektu mapowania pliku.|  
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|Wywołanie tej metody można utworzyć obiektu mapowania pliku, który zezwala na dostęp do wszystkich procesów.|  
|[CAtlFileMappingBase::OpenMapping](#openmapping)|Wywołanie tej metody, aby powrócić do dojścia do obiektu mapowania pliku.|  
|[CAtlFileMappingBase::Unmap](#unmap)|Wywołaj tę metodę, aby usunąć mapowanie obiektu mapowania pliku.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlFileMappingBase::operator =](#operator_eq)|Ustawia bieżący obiekt mapowania pliku do innego obiektu mapowania pliku.|  
  
## <a name="remarks"></a>Uwagi  
 Mapowanie plików jest skojarzenie zawartość pliku z części wirtualnej przestrzeni adresowej procesu. Ta klasa dostarcza metody do tworzenia obiektów mapowania pliku, pozwalające programy, aby łatwo uzyskiwać dostęp i udostępnianie danych.  
  
 Aby uzyskać więcej informacji, zobacz [mapowania pliku](http://msdn.microsoft.com/library/windows/desktop/aa366556) w zestawie Windows SDK.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlfile.h  
  
##  <a name="catlfilemappingbase"></a>  CAtlFileMappingBase::CAtlFileMappingBase  
 Konstruktor.  
  
```
CAtlFileMappingBase(CAtlFileMappingBase& orig);  
CAtlFileMappingBase() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `orig`  
 Oryginalny obiekt mapowanie plików do skopiowania można utworzyć nowego obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Tworzy nowy obiekt mapowania pliku, opcjonalnie przy użyciu istniejącego obiektu. Nadal należy wywołać [CAtlFileMappingBase::MapFile](#mapfile) próbę otwarcia lub utworzenia obiektu mapowania pliku dla pliku.  
  
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
 `orig`  
 Oryginalny obiekt mapowanie plików do skopiowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
##  <a name="getdata"></a>  CAtlFileMappingBase::GetData  
 Wywołaj tę metodę w celu pobrania danych z obiektu mapowania pliku.  
  
```
void* GetData() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do danych.  
  
##  <a name="gethandle"></a>  CAtlFileMappingBase::GetHandle  
 Wywołanie tej metody, aby powrócić do dojścia do obiektu mapowania pliku.  
  
```
HANDLE GetHandle() throw ();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca uchwyt do obiektu mapowania pliku.  
  
##  <a name="getmappingsize"></a>  CAtlFileMappingBase::GetMappingSize  
 Wywołanie tej metody można pobrać rozmiaru mapowania z obiektu mapowania pliku.  
  
```
SIZE_T GetMappingSize() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca rozmiar mapowania.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).  
  
##  <a name="mapfile"></a>  CAtlFileMappingBase::MapFile  
 Wywołaj tę metodę w celu otwarcia lub utworzenia obiektu mapowania pliku określonego pliku.  
  
```
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hFile`  
 Dojście do pliku, w którym można utworzyć obiektu mapowania. `hFile` musi być prawidłowy i nie można ustawić INVALID_HANDLE_VALUE.  
  
 `nMappingSize`  
 Rozmiar mapowania. 0, maksymalny rozmiar obiektu mapowania pliku jest taki sam, jak bieżący rozmiar pliku identyfikowane przez *hFile.*  
  
 `nOffset`  
 Przesunięcie w pliku mapowania w przypadku rozpoczęcia. Wartość przesunięcia musi być wielokrotnością liczby szczegółowości alokacji pamięci systemu.  
  
 `dwMappingProtection`  
 Ochrona żądany dla widoku pliku, gdy plik jest zamapowany. Zobacz `flProtect` w [funkcja CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537) w systemie Windows SDK.  
  
 `dwViewDesiredAccess`  
 Określa typ dostępu do widoku pliku i w związku z tym ochrony stron zamapowany przy użyciu pliku. Zobacz `dwDesiredAccess` w [MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763) w systemie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Po utworzeniu obiektu mapowania pliku, rozmiar pliku nie może przekraczać rozmiar obiektu mapowania pliku; Jeśli tak, nie wszystkie jego zawartość będą dostępne do udostępniania. Aby uzyskać więcej informacji, zobacz [funkcja CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537) i [MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).  
  
##  <a name="mapsharedmem"></a>  CAtlFileMappingBase::MapSharedMem  
 Wywołanie tej metody można utworzyć obiektu mapowania pliku, który zezwala na dostęp do wszystkich procesów.  
  
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
 `nMappingSize`  
 Rozmiar mapowania. W przypadku wartości 0 maksymalny rozmiar obiektu mapowania pliku jest równe rozmiarowi bieżącego obiektu mapowania pliku identyfikowane przez `szName.`  
  
 `szName`  
 Nazwa obiektu mapowania.  
  
 *pbAlreadyExisted*  
 Wskazuje wartość logiczna, która ma ustawioną wartość TRUE, jeśli mapowanie obiektu już istnieje.  
  
 `lpsa`  
 Wskaźnik do **SECURITY_ATTRIBUTES** struktury, która określa, czy zwrócone dojście mogą być dziedziczone przez procesy podrzędne. Zobacz *lpAttributes* w [funkcja CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537) w zestawie Windows SDK.  
  
 `dwMappingProtection`  
 Ochrona żądany dla widoku pliku, gdy plik jest zamapowany. Zobacz `flProtect` w **funkcja CreateFileMapping** w systemie Windows SDK.  
  
 `dwViewDesiredAccess`  
 Określa typ dostępu do widoku pliku i w związku z tym ochrony stron zamapowany przy użyciu pliku. Zobacz `dwDesiredAccess` w [MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763) w systemie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 **MapShareMem** umożliwia istniejącego obiektu mapowania pliku utworzonego przez [funkcja CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537), aby być udostępniane między procesami.  
  
##  <a name="openmapping"></a>  CAtlFileMappingBase::OpenMapping  
 Wywołanie tej metody, aby otworzyć nazwanego obiektu mapowania pliku określonego pliku.  
  
```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `szName`  
 Nazwa obiektu mapowania. Jeśli jest otwarte dojście do obiektu mapowania pliku o tej nazwie i deskryptora zabezpieczeń obiektu mapowania nie powoduje konfliktu z `dwViewDesiredAccess` operacja otwierania parametru zakończy się pomyślnie.  
  
 `nMappingSize`  
 Rozmiar mapowania. W przypadku wartości 0 maksymalny rozmiar obiektu mapowania pliku jest równe rozmiarowi bieżącego obiektu mapowania pliku identyfikowane przez `szName.`  
  
 `nOffset`  
 Przesunięcie w pliku mapowania w przypadku rozpoczęcia. Wartość przesunięcia musi być wielokrotnością liczby szczegółowości alokacji pamięci systemu.  
  
 `dwViewDesiredAccess`  
 Określa typ dostępu do widoku pliku i w związku z tym ochrony stron zamapowany przy użyciu pliku. Zobacz `dwDesiredAccess` w [MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763) w systemie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli parametry wejściowe są nieprawidłowe.  
  
##  <a name="operator_eq"></a>  CAtlFileMappingBase::operator =  
 Ustawia bieżący obiekt mapowania pliku do innego obiektu mapowania pliku.  
  
```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```  
  
### <a name="parameters"></a>Parametry  
 `orig`  
 Bieżący obiekt mapowania pliku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do bieżącego obiektu.  
  
##  <a name="unmap"></a>  CAtlFileMappingBase::Unmap  
 Wywołaj tę metodę, aby usunąć mapowanie obiektu mapowania pliku.  
  
```
HRESULT Unmap() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [UnmapViewOfFile](http://msdn.microsoft.com/library/windows/desktop/aa366882) w zestawie SDK systemu Windows, aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
