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
ms.openlocfilehash: 9e12e64041e38b8fa014815870132a75885014bf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496564"
---
# <a name="crtthreadtraits-class"></a>Klasa CRTThreadTraits

Ta klasa udostępnia funkcję tworzenia dla wątku CRT. Użyj tej klasy, jeśli wątek będzie używać funkcji CRT.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
class CRTThreadTraits
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRTThreadTraits:: onthread](#createthread)|Ruchom Wywołaj tę funkcję, aby utworzyć wątek, który może korzystać z funkcji CRT.|

## <a name="remarks"></a>Uwagi

Cechy wątku są klasami, które udostępniają funkcję tworzenia dla określonego typu wątku. Funkcja tworzenia ma ten sam podpis i semantykę co funkcja Windows myFunction [Thread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) .

Cechy wątku są używane przez następujące klasy:

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

Jeśli wątek nie będzie używać funkcji CRT, zamiast tego należy użyć [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md) .

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

##  <a name="createthread"></a>CRTThreadTraits:: onthread

Wywołaj tę funkcję, aby utworzyć wątek, który może korzystać z funkcji CRT.

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

Ta funkcja wywołuje [_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) do utworzenia wątku.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
