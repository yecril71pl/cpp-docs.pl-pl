---
title: Klasa CRTThreadTraits
ms.date: 11/04/2016
f1_keywords:
- CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits::CreateThread
helpviewer_keywords:
- CRTThreadTraits class
- threading [ATL], creation functions
- threading [ATL], CRT threads
ms.assetid: eb6e20b0-c2aa-4170-8e34-aaeeacc86343
ms.openlocfilehash: e5e13bad907e76968c4d4343e6617903e309e40f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278055"
---
# <a name="crtthreadtraits-class"></a>Klasa CRTThreadTraits

Ta klasa udostępnia funkcję tworzenia wątku CRT. Jeśli wątek będzie używać funkcji CRT, należy użyć tej klasy.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
class CRTThreadTraits
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRTThreadTraits::CreateThread](#createthread)|(Statyczny) Wywołaj tę funkcję, aby utworzyć wątek, można użyć funkcji CRT.|

## <a name="remarks"></a>Uwagi

Klasy, które zapewniają funkcję tworzenia dla określonego typu wątku z nich są cechami wątku. Funkcja tworzenia ma ten sam podpis i semantyka jako Windows [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) funkcji.

Cechy wątku są używane przez następujące klasy:

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

Jeśli wątek nie będzie korzystać z funkcji CRT, użyj [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md) zamiast tego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="createthread"></a>  CRTThreadTraits::CreateThread

Wywołaj tę funkcję, aby utworzyć wątek, można użyć funkcji CRT.

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

Ta funkcja wywołuje [_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) można utworzyć wątku.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)
