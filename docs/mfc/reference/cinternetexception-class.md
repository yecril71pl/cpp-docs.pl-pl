---
title: Klasa CInternetException
ms.date: 11/04/2016
f1_keywords:
- CInternetException
- AFXINET/CInternetException
- AFXINET/CInternetException::CInternetException
- AFXINET/CInternetException::m_dwContext
- AFXINET/CInternetException::m_dwError
helpviewer_keywords:
- CInternetException [MFC], CInternetException
- CInternetException [MFC], m_dwContext
- CInternetException [MFC], m_dwError
ms.assetid: 44fb3cbe-523e-4754-8843-a77909990b14
ms.openlocfilehash: b0239afa2b984ccf93d661ec11f11013c89fd912
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372405"
---
# <a name="cinternetexception-class"></a>Klasa CInternetException

Reprezentuje warunek wyjątku związane z operacją internetową.

## <a name="syntax"></a>Składnia

```
class CInternetException : public CException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInternetException::CInternetException](#cinternetexception)|Konstruuje `CInternetException` obiekt.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CInternetException::m_dwContext](#m_dwcontext)|Wartość kontekstu skojarzona z operacją, która spowodowała wyjątek.|
|[CInternetException::m_dwError](#m_dwerror)|Błąd, który spowodował wyjątek.|

## <a name="remarks"></a>Uwagi

Klasa `CInternetException` zawiera dwa elementy członkowskie danych publicznych: jeden zawiera kod błędu skojarzony z wyjątkiem, a drugi przechowuje identyfikator kontekstu aplikacji internetowej skojarzonej z błędem.

Aby uzyskać więcej informacji na temat identyfikatorów kontekstu dla aplikacji internetowych, zobacz artykuł [Programowanie internetowe z wininet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cexception](../../mfc/reference/cexception-class.md)

`CInternetException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

## <a name="cinternetexceptioncinternetexception"></a><a name="cinternetexception"></a>CInternetException::CInternetException

Ta funkcja elementu członkowskiego `CInternetException` jest wywoływana podczas tworzenia obiektu.

```
CInternetException(DWORD dwError);
```

### <a name="parameters"></a>Parametry

*dwError ( dwError )*<br/>
Błąd, który spowodował wyjątek.

### <a name="remarks"></a>Uwagi

Aby rzucić CInternetException, wywołać MFC globalnej funkcji [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception).

## <a name="cinternetexceptionm_dwcontext"></a><a name="m_dwcontext"></a>CInternetException::m_dwContext

Wartość kontekstu skojarzona z powiązaną operacją internetową.

```
DWORD_PTR m_dwContext;
```

### <a name="remarks"></a>Uwagi

Identyfikator kontekstu jest pierwotnie określony w [CInternetSession](../../mfc/reference/cinternetsession-class.md) i przekazywane przez MFC do [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)- i [CInternetFile](../../mfc/reference/cinternetfile-class.md)-klasy pochodne. Można zastąpić ten domyślny i przypisać dowolny parametr *dwContext* wartość wyboru. *dwContext* jest skojarzony z każdą operacją danego obiektu. *dwContext* identyfikuje informacje o stanie operacji zwrócone przez [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).

## <a name="cinternetexceptionm_dwerror"></a><a name="m_dwerror"></a>CInternetException::m_dwError

Błąd, który spowodował wyjątek.

```
DWORD m_dwError;
```

### <a name="remarks"></a>Uwagi

Ta wartość błędu może być kodem błędu systemu, znalezionym w WINERROR. H lub wartość błędu z WININET. H.

Aby uzyskać listę kodów błędów Win32, zobacz [Kody błędów](/windows/win32/Debug/system-error-codes). Aby uzyskać listę komunikatów o błędach specyficznych dla Internetu, zobacz . Oba tematy znajdują się w windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CException](../../mfc/reference/cexception-class.md)
