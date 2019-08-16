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
ms.openlocfilehash: d086a42f5dcdf005d10c8853776da66b691a8e11
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495474"
---
# <a name="win32threadtraits-class"></a>Klasa Win32ThreadTraits

Ta klasa udostępnia funkcję tworzenia dla wątku systemu Windows. Użyj tej klasy, jeśli wątek nie będzie używać funkcji CRT.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
class Win32ThreadTraits
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Win32ThreadTraits:: onthread](#createthread)|Ruchom Wywołaj tę funkcję, aby utworzyć wątek, który nie powinien używać funkcji CRT.|

## <a name="remarks"></a>Uwagi

Cechy wątku są klasami, które udostępniają funkcję tworzenia dla określonego typu wątku. Funkcja tworzenia ma ten sam podpis i semantykę co funkcja Windows myFunction [Thread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) .

Cechy wątku są używane przez następujące klasy:

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

Jeśli wątek będzie używać funkcji CRT, zamiast tego należy użyć [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) .

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

##  <a name="createthread"></a>Win32ThreadTraits:: onthread

Wywołaj tę funkcję, aby utworzyć wątek, który nie powinien używać funkcji CRT.

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

*dwStackSize*<br/>
Rozmiar stosu dla nowego wątku.

*pfnThreadProc*<br/>
Procedura wątku nowego wątku.

*pvParam*<br/>
Parametr, który ma zostać przesłany do procedury wątku.

*dwCreationFlags*<br/>
Flagi tworzenia (0 lub CREATE_SUSPENDED).

*pdwThreadId*<br/>
określoną Adres zmiennej typu DWORD, która po powodzeniu odbiera identyfikator wątku nowo utworzonego wątku.

### <a name="return-value"></a>Wartość zwracana

Zwraca dojście do nowo utworzonego wątku lub wartości NULL w przypadku niepowodzenia. Wywołaj funkcję [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby uzyskać rozszerzone informacje o błędzie.

### <a name="remarks"></a>Uwagi

Aby [](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) uzyskać więcej informacji na temat parametrów tej funkcji, zobacz myFunction.

Ta funkcja wywołuje `CreateThread` do utworzenia wątku.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
