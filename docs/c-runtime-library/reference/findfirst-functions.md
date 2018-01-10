---
title: "_findfirst —, _findfirst32 —, _findfirst32i64 —, _findfirst64 —, _findfirst64i32 —, _findfirsti64 —, _wfindfirst —, _wfindfirst32 —, _wfindfirst32i64 —, _wfindfirst64 —, _wfindfirst64i32 —, _wfindfirsti64 — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _findfirst
- _wfindfirst
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- findfirst32i64
- wfindfirst32i64
- tfindfirst64
- _findfirst64i32
- _wfindfirst32i64
- _wfindfirsti64
- wfindfirst
- _tfindfirsti64
- findfirst32
- _tfindfirst32
- _findfirsti64
- findfirst
- wfindfirst64
- wfindfirst32
- tfindfirst32
- _wfindfirst64i32
- findfirst64i32
- tfindfirst64i32
- _wfindfirst
- findfirsti64
- _findfirst32i64
- wfindfirst64i32
- _wfindfirst32
- _findfirst32
- _tfindfirst32i64
- tfindfirst
- _tfindfirst64i32
- findfirst64
- _tfindfirst
- _findfirst64
- _tfindfirst64
- tfindfirst32i64
- _findfirst
- _wfindfirst64
dev_langs: C++
helpviewer_keywords:
- _tfindfirst64 function
- _wfindfirst64i32 function
- _wfindfirst32i64 function
- wfindfirst32 function
- _findfirst function
- wfindfirst64 function
- _wfindfirst function
- _findfirst64i32 function
- wfindfirst function
- _findfirst64 function
- tfindfirst32 function
- _tfindfirst64i32 function
- findfirst function
- findfirst32i64 function
- tfindfirst64 function
- _tfindfirst32 function
- tfindfirst32i64 function
- tfindfirst64i32 function
- _wfindfirsti64 function
- _findfirst32i64 function
- findfirst32 function
- findfirsti64 function
- findfirst64i32 function
- tfindfirsti64 function
- tfindfirst function
- _wfindfirst32 function
- wfindfirsti64 function
- _tfindfirsti64 function
- _tfindfirst function
- _tfindfirst32i64 function
- findfirst64 function
- _findfirst32 function
- _findfirsti64 function
- wfindfirst32i64 function
- wfindfirst64i32 function
- _wfindfirst64 function
ms.assetid: 9bb46d1a-b946-47de-845a-a0b109a33ead
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9f95b4097f2e0ddd399df9b65ed178c1423edaaa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="findfirst-findfirst32-findfirst32i64-findfirst64-findfirst64i32-findfirsti64-wfindfirst-wfindfirst32-wfindfirst32i64-wfindfirst64-wfindfirst64i32-wfindfirsti64"></a>_findfirst — _findfirst32 —, _findfirst32i64 —, _findfirst64 —, _findfirst64i32 —, _findfirsti64 —, _wfindfirst —, _wfindfirst32 —, _wfindfirst32i64 —, _wfindfirst64 —, _wfindfirst64i32 —, _wfindfirsti64 —
Zawierają informacje dotyczące pierwszego wystąpienia nazwy pliku, który pasuje do pliku określonego w `filespec` argumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
intptr_t _findfirst(  
   const char *filespec,  
   struct _finddata_t *fileinfo   
);  
intptr_t _findfirst32(  
   const char *filespec,  
   struct _finddata32_t *fileinfo   
);  
intptr_t _findfirst64(  
   const char *filespec,  
   struct _finddata64_t *fileinfo   
);  
intptr_t _findfirsti64(  
   const char *filespec,  
   struct _finddatai64_t *fileinfo   
);  
intptr_t _findfirst32i64(  
   const char *filespec,  
   struct _finddata32i64_t *fileinfo   
);  
intptr_t _findfirst64i32(  
   const char *filespec,  
   struct _finddata64i32_t *fileinfo   
);  
intptr_t _wfindfirst(  
   const wchar_t *filespec,  
   struct _wfinddata_t *fileinfo   
);  
intptr_t _wfindfirst32(  
   const wchar_t *filespec,  
   struct _wfinddata32_t *fileinfo   
);  
intptr_t _wfindfirst64(  
   const wchar_t *filespec,  
   struct _wfinddata64_t *fileinfo   
);  
intptr_t _wfindfirsti64(  
   const wchar_t *filespec,  
   struct _wfinddatai64_t *fileinfo   
);  
intptr_t _wfindfirst32i64(  
   const wchar_t *filespec,  
   struct _wfinddata32i64_t *fileinfo   
);  
intptr_t _wfindfirst64i32(  
   const wchar_t *filespec,  
   struct _wfinddata64i32_t *fileinfo   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `filespec`  
 Specyfikacja pliku docelowego (mogą zawierać symbole wieloznaczne).  
  
 `fileinfo`  
 Bufor informacji o pliku.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia `_findfirst` zwraca uchwyt unikatowe wyszukiwanie identyfikowanie pliku lub grupy plików, które pasują `filespec` specyfikacji, którego można użyć w kolejnych wywołaniu [_findnext —](../../c-runtime-library/reference/findnext-functions.md) lub `_findclose`. W przeciwnym razie `_findfirst` zwraca wartość -1 i ustawia `errno` do jednej z następujących wartości.  
  
 `EINVAL`  
 Nieprawidłowy parametr: `filespec` lub `fileinfo` został `NULL`. Lub system operacyjny zwrócił nieoczekiwany błąd.  
  
 `ENOENT`  
 Specyfikacja pliku, którego nie można dopasować.  
  
 `ENOMEM`  
 Za mało pamięci.  
  
 `EINVAL`  
 Specyfikacja nazwy nieprawidłowy plik lub podana nazwa pliku jest większy niż `MAX_PATH`.  
  
 Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Jeśli przekazano nieprawidłowy parametr tych funkcji Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md).  
  
## <a name="remarks"></a>Uwagi  
 Należy wywołać [_findclose —](../../c-runtime-library/reference/findclose.md) po zakończeniu pracy w trybie `_findfirst` lub `_findnext` — funkcja (lub warianty). To zwalnia zasoby używane przez te funkcje w aplikacji.  
  
 Zmiany te funkcje, które mają `w` prefiks są wersje znaków dwubajtowych; w przeciwnym razie są one takie same jak odpowiednie funkcje jednobajtowe.  
  
 Zmiany tych funkcji obsługuje typy czasu 32-bitowy lub 64-bitowej i rozmiary plików 32-bitowy lub 64-bitowej. Pierwszy sufiks numeryczny (`32` lub `64`) wskazuje rozmiar typu time; jest drugi sufiks `i32` lub `i64`oraz wskazuje, czy rozmiar pliku jest reprezentowany jako 32-bitowy lub 64-bitowej liczby całkowitej. Aby uzyskać informacje o tym, które wersje obsługują typy czasu 32-bitowe i 64-bitowe i rozmiary plików Zobacz poniższą tabelę. `i32` Lub `i64` sufiks zostanie pominięty, jeśli jest taka sama jak rozmiar typu time, więc `_findfirst64` długości 64-bitowy plik obsługuje także i `_findfirst32` obsługuje tylko 32-bitowy plik długości.  
  
 Te funkcje użycie różnych metod `_finddata_t` struktury `fileinfo` parametru. Aby uzyskać więcej informacji na temat struktury, zobacz [funkcje wyszukiwania Filename](../../c-runtime-library/filename-search-functions.md).  
  
 Zmiany, używające typu czasu 64-bitowych Włącz daty utworzenia pliku wyrażane się za pośrednictwem 23:59:59 31 grudnia 3000 UTC. Używające typy czasu 32-bitowych reprezentują dat tylko za pośrednictwem 23:59:59 18 stycznia 2038 r., UTC. Północy, 1 stycznia 1970 jest dolna granica zakresu dat dla tych funkcji.  
  
 Jeśli nie masz powód, aby użyć wersji, które jawnie określ rozmiar w czasie, użyj `_findfirst` lub `_wfindfirst` lub, jeśli zachodzi potrzeba obsługi rozmiary plików większych niż 3 GB, użyj `_findfirsti64` lub `_wfindfirsti64`. Wszystkie te funkcje Użyj typu czasu 64-bitowych. We wcześniejszych wersjach te funkcje używane typu czasu 32-bitowych. Jeśli jest to istotne zmiany dla aplikacji, można zdefiniować `_USE_32BIT_TIME_T` można przywrócić poprzednie działanie. Jeśli `_USE_32BIT_TIME_T` jest zdefiniowany, `_findfirst`, `_finfirsti64`, i odpowiadające im wersje Unicode, użyj czasu 32-bitowych.  
  
### <a name="time-type-and-file-length-type-variations-of-findfirst"></a>Typ czasu i zmian typu długość pliku _findfirst —  
  
|Funkcje|`_USE_32BIT_TIME_T`Definicja?|Typu czasu|Typ długość pliku|  
|---------------|----------------------------------|---------------|----------------------|  
|`_findfirst`, `_wfindfirst`|Nie zdefiniowano|64-bitowy|32-bitowa|  
|`_findfirst`, `_wfindfirst`|Definicja|32-bitowa|32-bitowa|  
|`_findfirst32`, `_wfindfirst32`|Nie dotyczy definicji makra|32-bitowa|32-bitowa|  
|`_findfirst64`, `_wfindfirst64`|Nie dotyczy definicji makra|64-bitowy|64-bitowy|  
|`_findfirsti64`, `_wfindfirsti64`|Nie zdefiniowano|64-bitowy|64-bitowy|  
|`_findfirsti64`, `_wfindfirsti64`|Definicja|32-bitowa|64-bitowy|  
|`_findfirst32i64`, `_wfindfirst32i64`|Nie dotyczy definicji makra|32-bitowa|64-bitowy|  
|`_findfirst64i32`, `_wfindfirst64i32`|Nie dotyczy definicji makra|64-bitowy|32-bitowa|  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tfindfirst`|`_findfirst`|`_findfirst`|`_wfindfirst`|  
|`_tfindfirst32`|`_findfirst32`|`_findfirst32`|`_wfindfirst32`|  
|`_tfindfirst64`|`_findfirst64`|`_findfirst64`|`_wfindfirst64`|  
|`_tfindfirsti64`|`_findfirsti64`|`_findfirsti64`|`_wfindfirsti64`|  
|`_tfindfirst32i64`|`_findfirst32i64`|`_findfirst32i64`|`_wfindfirst32i64`|  
|`_tfindfirst64i32`|`_findfirst64i32`|`_findfirst64i32`|`_wfindfirst64i32`|  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`_findfirst`|\<IO.h >|  
|`_findfirst32`|\<IO.h >|  
|`_findfirst64`|\<IO.h >|  
|`_findfirsti64`|\<IO.h >|  
|`_findfirst32i64`|\<IO.h >|  
|`_findfirst64i32`|\<IO.h >|  
|`_wfindfirst`|\<IO.h > lub \<wchar.h >|  
|`_wfindfirst32`|\<IO.h > lub \<wchar.h >|  
|`_wfindfirst64`|\<IO.h > lub \<wchar.h >|  
|`_wfindfirsti64`|\<IO.h > lub \<wchar.h >|  
|`_wfindfirst32i64`|\<IO.h > lub \<wchar.h >|  
|`_wfindfirst64i32`|\<IO.h > lub \<wchar.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wywołania systemowe](../../c-runtime-library/system-calls.md)   
 [Funkcje wyszukiwania nazwy pliku](../../c-runtime-library/filename-search-functions.md)