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
ms.openlocfilehash: da4b8b3d5a41ab16dc2027fd632c56158afd3b97
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57288743"
---
# <a name="win32threadtraits-class"></a>Klasa Win32ThreadTraits

Ta klasa udostępnia funkcję tworzenia wątku Windows. Jeśli wątek nie użyje funkcji CRT, należy użyć tej klasy.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
class Win32ThreadTraits
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Win32ThreadTraits::CreateThread](#createthread)|(Statyczny) Wywołaj tę funkcję, aby utworzyć wątek, który nie należy używać funkcji CRT.|

## <a name="remarks"></a>Uwagi

Klasy, które zapewniają funkcję tworzenia dla określonego typu wątku z nich są cechami wątku. Funkcja tworzenia ma ten sam podpis i semantyka jako Windows [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) funkcji.

Cechy wątku są używane przez następujące klasy:

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

Jeśli wątek będzie używać funkcji CRT, użyj [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) zamiast tego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="createthread"></a>  Win32ThreadTraits::CreateThread

Wywołaj tę funkcję, aby utworzyć wątek, który nie należy używać funkcji CRT.

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
Parametr, który zostanie przekazany do procedury wątku.

*dwCreationFlags*<br/>
Tworzenie flagi (0 lub CREATE_SUSPENDED).

*pdwThreadId*<br/>
[out] Adres zmiennej typu DWORD, że w przypadku powodzenia odbiera identyfikator wątku dla nowo utworzonego wątku.

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt do nowo utworzonego wątku lub wartość NULL w przypadku niepowodzenia. Wywołaj [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) Aby uzyskać rozszerzone informacje o błędzie.

### <a name="remarks"></a>Uwagi

Zobacz [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) więcej informacji na temat parametrów dotyczących wyłącznie tej funkcji.

Ta funkcja wywołuje `CreateThread` można utworzyć wątku.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)
