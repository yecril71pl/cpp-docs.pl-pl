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
ms.openlocfilehash: c4f4c7a5b7594270aff9dfbc224e9a66ba09be3f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505904"
---
# <a name="cinternetexception-class"></a>Klasa CInternetException

Reprezentuje warunek wyjątku związany z operacją internetową.

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

`CInternetException` Klasa zawiera dwa publiczne elementy członkowskie danych: jeden zawiera kod błędu skojarzony z wyjątkiem, a drugi zawiera identyfikator kontekstu aplikacji internetowej skojarzonej z błędem.

Aby uzyskać więcej informacji o identyfikatorach kontekstu dla aplikacji internetowych, zobacz artykuł [programowanie internetowe za pomocą usługi WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CInternetException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet. h

##  <a name="cinternetexception"></a>CInternetException::CInternetException

Ta funkcja członkowska jest wywoływana, `CInternetException` gdy obiekt zostanie utworzony.

```
CInternetException(DWORD dwError);
```

### <a name="parameters"></a>Parametry

*Elemencie*<br/>
Błąd, który spowodował wyjątek.

### <a name="remarks"></a>Uwagi

Aby zgłosić CInternetException, wywołaj globalną funkcję MFC [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception).

##  <a name="m_dwcontext"></a>CInternetException::m_dwContext

Wartość kontekstu skojarzona z pokrewną operacją internetową.

```
DWORD_PTR m_dwContext;
```

### <a name="remarks"></a>Uwagi

Identyfikator kontekstu jest pierwotnie określony w [CInternetSession](../../mfc/reference/cinternetsession-class.md) i przesłany przez MFC do klas pochodnych [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)i [CInternetFile](../../mfc/reference/cinternetfile-class.md). Można zastąpić to ustawienie domyślne i przypisać dowolny parametr *dwContext* wybraną wartość. *dwContext* jest skojarzony z żadną operacją danego obiektu. *dwContext* identyfikuje informacje o stanie operacji zwrócone przez [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).

##  <a name="m_dwerror"></a>CInternetException::m_dwError

Błąd, który spowodował wyjątek.

```
DWORD m_dwError;
```

### <a name="remarks"></a>Uwagi

Ta wartość błędu może być kodem błędu systemu, który znajduje się w WINERROR. H lub wartość błędu z WININET. C.

Aby uzyskać listę kodów błędów Win32, zobacz [kody błędów](/windows/win32/Debug/system-error-codes). Lista komunikatów o błędach specyficznych dla Internetu znajduje się w temacie. Oba tematy znajdują się w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CException](../../mfc/reference/cexception-class.md)
