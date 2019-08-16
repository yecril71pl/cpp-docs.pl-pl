---
title: CComGITPtr Class
ms.date: 11/04/2016
f1_keywords:
- CComGITPtr
- ATLBASE/ATL::CComGITPtr
- ATLBASE/ATL::CComGITPtr::CComGITPtr
- ATLBASE/ATL::CComGITPtr::Attach
- ATLBASE/ATL::CComGITPtr::CopyTo
- ATLBASE/ATL::CComGITPtr::Detach
- ATLBASE/ATL::CComGITPtr::GetCookie
- ATLBASE/ATL::CComGITPtr::Revoke
- ATLBASE/ATL::CComGITPtr::m_dwCookie
helpviewer_keywords:
- CComGITPtr class
ms.assetid: af895acb-525a-4555-bb67-b241b7df515b
ms.openlocfilehash: 00265cc445191a5a539ab21d6f64b255849495e9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497267"
---
# <a name="ccomgitptr-class"></a>CComGITPtr Class

Ta klasa dostarcza metody do pracy z wskaźnikami interfejsu i globalną tabelą interfejsów (GIT).

## <a name="syntax"></a>Składnia

```
template <class T>
class CComGITPtr
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ wskaźnika interfejsu, który ma być przechowywany w usłudze GIT.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComGITPtr::CComGITPtr](#ccomgitptr)|Konstruktor.|
|[CComGITPtr::~CComGITPtr](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComGITPtr::Attach](#attach)|Wywołaj tę metodę, aby zarejestrować wskaźnik interfejsu w globalnej tabeli interfejsów (GIT).|
|[CComGITPtr::CopyTo](#copyto)|Wywołaj tę metodę, aby skopiować interfejs z tabeli interfejsu globalnego (GIT) do porzuconego wskaźnika.|
|[CComGITPtr::Detach](#detach)|Wywołaj tę metodę, aby usunąć skojarzenie `CComGITPtr` interfejsu z obiektu.|
|[CComGITPtr::GetCookie](#getcookie)|Wywołaj tę metodę, aby zwrócić plik cookie `CComGITPtr` z obiektu.|
|[CComGITPtr::Revoke](#revoke)|Wywołaj tę metodę, aby usunąć interfejs z globalnej tabeli interfejsu (GIT).|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComGITPtr:: operator DWORD](#operator_dword)|Zwraca plik cookie z `CComGITPtr` obiektu.|
|[CComGITPtr::operator =](#operator_eq)|Operator przypisania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComGITPtr::m_dwCookie](#m_dwcookie)|Plik cookie.|

## <a name="remarks"></a>Uwagi

Obiekty, które agregują organizatora wolnego wątku i muszą używać wskaźników interfejsu uzyskanych z innych obiektów, muszą wykonać dodatkowe czynności, aby upewnić się, że interfejsy są prawidłowo organizowane. Zwykle obejmuje to przechowywanie wskaźników interfejsu w narzędziu GIT i pobieranie wskaźnika z narzędzia GIT przy każdym jego użyciu. Klasa `CComGITPtr` jest dostarczana, aby ułatwić korzystanie ze wskaźników interfejsu przechowywanych w usłudze git.

> [!NOTE]
>  Globalna tabela interfejsu jest dostępna tylko w systemie Windows 95 z modelem DCOM w wersji 1,1 lub nowszej, Windows 98, Windows NT 4,0 z dodatkiem Service Pack 3 lub nowszym oraz Windows 2000.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

##  <a name="attach"></a>  CComGITPtr::Attach

Wywołaj tę metodę, aby zarejestrować wskaźnik interfejsu w globalnej tabeli interfejsów (GIT).

```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik interfejsu, który ma zostać dodany do usługi GIT.

*dwCookie*<br/>
Plik cookie służący do identyfikowania wskaźnika interfejsu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli GIT jest nieprawidłowy lub jeśli plik cookie ma wartość NULL.

##  <a name="ccomgitptr"></a>  CComGITPtr::CComGITPtr

Konstruktor.

```
CComGITPtr() throw();
CComGITPtr(T* p);
CComGITPtr(const CComGITPtr& git);
explicit CComGITPtr(DWORD dwCookie) throw();
CComGITPtr(CComGITPtr&& rv);
```

### <a name="parameters"></a>Parametry

*p*<br/>
podczas Wskaźnik interfejsu, który ma być przechowywany w globalnej tabeli interfejsów (GIT).

*narzędzia*<br/>
podczas Odwołanie do istniejącego `CComGITPtr` obiektu.

*dwCookie*<br/>
podczas Plik cookie służący do identyfikowania wskaźnika interfejsu.

*rv*<br/>
podczas Obiekt źródłowy `CComGITPtr` , z którego mają zostać przeniesione dane.

### <a name="remarks"></a>Uwagi

Tworzy nowy `CComGITPtr` obiekt, opcjonalnie używając istniejącego `CComGITPtr` obiektu.

Konstruktor wykorzystujący *RV* to Konstruktor przenoszący. Dane są przenoszone ze źródła, *RV*, a następnie *RV* jest wyczyszczone.

##  <a name="dtor"></a>  CComGITPtr::~CComGITPtr

Destruktor.

```
~CComGITPtr() throw();
```

### <a name="remarks"></a>Uwagi

Usuwa interfejs z globalnej tabeli interfejsu (GIT) przy użyciu [CComGITPtr:: Revoke](#revoke).

##  <a name="copyto"></a>CComGITPtr:: CopyTo

Wywołaj tę metodę, aby skopiować interfejs z tabeli interfejsu globalnego (GIT) do porzuconego wskaźnika.

```
HRESULT CopyTo(T** pp) const throw();
```

### <a name="parameters"></a>Parametry

*miesięcznie*<br/>
Wskaźnik, który ma otrzymać interfejs.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Interfejs z GIT jest kopiowany do przenoszonego wskaźnika. Wskaźnik musi zostać wydzierżawiony przez obiekt wywołujący, gdy nie jest już wymagany.

##  <a name="detach"></a>  CComGITPtr::Detach

Wywołaj tę metodę, aby usunąć skojarzenie `CComGITPtr` interfejsu z obiektu.

```
DWORD Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca plik cookie z `CComGITPtr` obiektu.

### <a name="remarks"></a>Uwagi

Obiekt wywołujący może usunąć interfejs z usługi GIT przy użyciu [CComGITPtr:: Revoke](#revoke).

##  <a name="getcookie"></a>  CComGITPtr::GetCookie

Wywołaj tę metodę, aby zwrócić plik cookie `CComGITPtr` z obiektu.

```
DWORD GetCookie() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca plik cookie.

### <a name="remarks"></a>Uwagi

Plik cookie jest zmienną służącą do identyfikowania interfejsu i jego lokalizacji.

##  <a name="m_dwcookie"></a>  CComGITPtr::m_dwCookie

Plik cookie.

```
DWORD m_dwCookie;
```

### <a name="remarks"></a>Uwagi

Plik cookie jest zmienną członkowską używaną do identyfikowania interfejsu i jego lokalizacji.

##  <a name="operator_eq"></a>CComGITPtr:: operator =

Operator przypisania.

```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```

### <a name="parameters"></a>Parametry

*p*<br/>
podczas Wskaźnik do interfejsu.

*narzędzia*<br/>
podczas Odwołanie do `CComGITPtr` obiektu.

*dwCookie*<br/>
podczas Plik cookie służący do identyfikowania wskaźnika interfejsu.

*rv*<br/>
podczas , `CComGITPtr` Aby przenieść dane z.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CComGITPtr` obiekt.

### <a name="remarks"></a>Uwagi

Przypisuje nową wartość do `CComGITPtr` obiektu, z istniejącego obiektu lub z odwołania do globalnej tabeli interfejsów.

##  <a name="operator_dword"></a>CComGITPtr:: operator DWORD

Zwraca plik cookie skojarzony z `CComGITPtr` obiektem.

```
operator DWORD() const;
```

### <a name="remarks"></a>Uwagi

Plik cookie jest zmienną służącą do identyfikowania interfejsu i jego lokalizacji.

##  <a name="revoke"></a>CComGITPtr:: odwołaj

Wywołaj tę metodę, aby usunąć bieżący interfejs z globalnej tabeli interfejsu (GIT).

```
HRESULT Revoke() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Usuwa interfejs z usługi GIT.

## <a name="see-also"></a>Zobacz także

[Organizator trybu wolnych wątków](../../atl/atl-and-the-free-threaded-marshaler.md)<br/>
[Uzyskiwanie dostępu do interfejsów w apartamentach](/windows/win32/com/accessing-interfaces-across-apartments)<br/>
[Kiedy używać globalnej tabeli interfejsów](/windows/win32/com/when-to-use-the-global-interface-table)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
