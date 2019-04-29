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
ms.openlocfilehash: dedf8926f02dd36dc8d6ac8ab5ff4056b60dfc91
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345711"
---
# <a name="cinternetexception-class"></a>Klasa CInternetException

Przedstawia warunek wyjątku związany z operacją Internet.

## <a name="syntax"></a>Składnia

```
class CInternetException : public CException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInternetException::CInternetException](#cinternetexception)|Konstruuje `CInternetException` obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CInternetException::m_dwContext](#m_dwcontext)|Wartość kontekstu skojarzone z operacją, który spowodował wyjątek.|
|[CInternetException::m_dwError](#m_dwerror)|Błąd, który spowodował wyjątek.|

## <a name="remarks"></a>Uwagi

`CInternetException` Klasa zawiera dwa publiczne elementy członkowskie danych: jeden posiada skojarzony z wyjątkiem kod błędu:, a drugi zawiera identyfikator kontekstu w aplikacji internetowej skojarzony z błędem.

Aby uzyskać więcej informacji na temat identyfikatorów kontekstu dla aplikacji internetowych, zobacz artykuł [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CInternetException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

##  <a name="cinternetexception"></a>  CInternetException::CInternetException

Ta funkcja członkowska jest wywoływana, gdy `CInternetException` obiekt zostanie utworzony.

```
CInternetException(DWORD dwError);
```

### <a name="parameters"></a>Parametry

*dwError*<br/>
Błąd, który spowodował wyjątek.

### <a name="remarks"></a>Uwagi

Zgłoszenie CInternetException, wywołaj funkcję globalne MFC [afxthrowinternetexception —](internet-url-parsing-globals.md#afxthrowinternetexception).

##  <a name="m_dwcontext"></a>  CInternetException::m_dwContext

Wartość kontekstu skojarzone z operacji dotyczącej Internet.

```
DWORD_PTR m_dwContext;
```

### <a name="remarks"></a>Uwagi

W pierwotnie określono identyfikator kontekstu [CInternetSession](../../mfc/reference/cinternetsession-class.md) i przekazywany przez MFC, aby [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)— i [CInternetFile](../../mfc/reference/cinternetfile-class.md)-klas pochodnych. Możesz zastąpić to ustawienie domyślne i przypisać dowolny *dwContext* parametru wybranej wartości. *dwContext* jest skojarzony z wszelkich operacji danego obiektu. *dwContext* określa informacje o stanie operacji zwrócony przez [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).

##  <a name="m_dwerror"></a>  CInternetException::m_dwError

Błąd, który spowodował wyjątek.

```
DWORD m_dwError;
```

### <a name="remarks"></a>Uwagi

Ta wartość błędu może być systemem znaleziono w powiodło się. kod błędu. H, lub wartość błędu z WININET. H.

Aby uzyskać listę kodów błędów systemu Win32, zobacz [kody błędów](/windows/desktop/Debug/system-error-codes). Aby uzyskać listę komunikatów o błędach specyficzne dla Internetu Zobacz. Zarówno tematy znajdują się w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CException](../../mfc/reference/cexception-class.md)
