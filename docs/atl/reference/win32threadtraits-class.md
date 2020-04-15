---
title: Klasa Win32ThreadTraits
ms.date: 11/04/2016
f1_keywords:
- Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits::CreateThread
helpviewer_keywords:
- threading [ATL], Windows threads
- threading [ATL], creation functions
- Win32ThreadTraits class
ms.assetid: 50279c38-eae1-4301-9ea6-97ccea580f3e
ms.openlocfilehash: 64f02293508894a70f36c29d5032c9ba8f250c38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325802"
---
# <a name="win32threadtraits-class"></a>Klasa Win32ThreadTraits

Ta klasa zapewnia funkcję tworzenia dla wątku systemu Windows. Użyj tej klasy, jeśli wątek nie będzie używać funkcji CRT.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class Win32ThreadTraits
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Win32ThreadTraits::CreateThread](#createthread)|(Statyczne) Wywołanie tej funkcji, aby utworzyć wątek, który nie powinien używać funkcji CRT.|

## <a name="remarks"></a>Uwagi

Cechy wątku są klasy, które zapewniają funkcję tworzenia dla określonego typu wątku. Funkcja tworzenia ma ten sam podpis i semantyki jak funkcja [Tworzenia Wtłaczu](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) systemu Windows.

Cechy wątku są używane przez następujące klasy:

- [Cthreadpool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread (Wąwozie)](../../atl/reference/cworkerthread-class.md)

Jeśli wątek będzie używał funkcji CRT, użyj [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) zamiast tego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="win32threadtraitscreatethread"></a><a name="createthread"></a>Win32ThreadTraits::CreateThread

Wywołanie tej funkcji, aby utworzyć wątek, który nie powinien używać funkcji CRT.

```
static HANDLE CreateThread(
    LPSECURITY_ATTRIBUTES lpsa,
    DWORD dwStackSize,
    LPTHREAD_START_ROUTINE pfnThreadProc,
    void* pvParam,
    DWORD dwCreationFlags,
    DWORD* pdwThreadId) throw();
```

### <a name="parameters"></a>Parametry

*lpsa*<br/>
Atrybuty zabezpieczeń dla nowego wątku.

*rozmiar dwStackSize*<br/>
Rozmiar stosu dla nowego wątku.

*pfnThreadProc*<br/>
Procedura gwintu nowego wątku.

*pvParam*<br/>
Parametr, który ma zostać przekazany do procedury wątku.

*dwCreationFlags*<br/>
Flagi tworzenia (0 lub CREATE_SUSPENDED).

*pdwWydanie*<br/>
[na zewnątrz] Adres zmiennej DWORD, która po powodzenie odbiera identyfikator wątku nowo utworzonego wątku.

### <a name="return-value"></a>Wartość zwracana

Zwraca dojście do nowo utworzonego wątku lub NULL w przypadku awarii. Wywołanie [GetLastError,](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aby uzyskać rozszerzone informacje o błędzie.

### <a name="remarks"></a>Uwagi

Zobacz [CreateThread aby](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) uzyskać więcej informacji na temat parametrów tej funkcji.

Ta funkcja `CreateThread` wywołuje, aby utworzyć wątek.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
