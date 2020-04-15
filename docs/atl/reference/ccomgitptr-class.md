---
title: Klasa CComGITPtr
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
ms.openlocfilehash: 230eeb1577189d2057e530e1df8ef99c611fb32b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327837"
---
# <a name="ccomgitptr-class"></a>Klasa CComGITPtr

Ta klasa zawiera metody radzenia sobie ze wskaźnikami interfejsu i tabelą interfejsu globalnego (GIT).

## <a name="syntax"></a>Składnia

```
template <class T>
class CComGITPtr
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ wskaźnika interfejsu, który ma być przechowywany w GIT.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComGITPtr::CComGITPtr](#ccomgitptr)|Konstruktor.|
|[CComGITPtr::~CComGITPtr](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComGITPtr::Dołącz](#attach)|Wywołanie tej metody, aby zarejestrować wskaźnik interfejsu w globalnej tabeli interfejsu (GIT).|
|[CComGITPtr::CopyTo](#copyto)|Wywołanie tej metody, aby skopiować interfejs z tabeli interfejsu globalnego (GIT) do przekazanego wskaźnika.|
|[CComGITPtr::Detach](#detach)|Wywołanie tej metody, aby odłączyć `CComGITPtr` interfejs od obiektu.|
|[CComGITPtr::GetCookie](#getcookie)|Wywołanie tej metody, aby `CComGITPtr` zwrócić plik cookie z obiektu.|
|[CComGITPtr::Odwołaj](#revoke)|Wywołanie tej metody, aby usunąć interfejs z tabeli interfejsu globalnego (GIT).|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComGITPtr::operator DWORD](#operator_dword)|Zwraca plik cookie `CComGITPtr` z obiektu.|
|[CComGITPtr::operator =](#operator_eq)|Operator przypisania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComGITPtr::m_dwCookie](#m_dwcookie)|Plik cookie.|

## <a name="remarks"></a>Uwagi

Obiekty, które agregują free threaded organizatora i trzeba użyć wskaźników interfejsu uzyskanych z innych obiektów należy podjąć dodatkowe kroki, aby upewnić się, że interfejsy są poprawnie zorganizowane. Zazwyczaj obejmuje to przechowywanie wskaźników interfejsu w GIT i uzyskiwanie wskaźnika z GIT za każdym razem, gdy jest używany. Klasa `CComGITPtr` jest dostępna, aby ułatwić korzystanie ze wskaźników interfejsu przechowywanych w GIT.

> [!NOTE]
> Funkcja tabeli interfejsu globalnego jest dostępna tylko w systemie Windows 95 w wersji DCOM 1.1 i nowszej, systemie Windows 98, windows NT 4.0 z dodatkiem Service Pack 3 i nowszym oraz systemie Windows 2000.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="ccomgitptrattach"></a><a name="attach"></a>CComGITPtr::Dołącz

Wywołanie tej metody, aby zarejestrować wskaźnik interfejsu w globalnej tabeli interfejsu (GIT).

```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Wskaźnik interfejsu, który ma zostać dodany do GIT.

*dwCookie (właśc.*<br/>
Plik cookie używany do identyfikowania wskaźnika interfejsu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli GIT jest nieprawidłowy lub jeśli plik cookie jest równy null.

## <a name="ccomgitptrccomgitptr"></a><a name="ccomgitptr"></a>CComGITPtr::CComGITPtr

Konstruktor.

```
CComGITPtr() throw();
CComGITPtr(T* p);
CComGITPtr(const CComGITPtr& git);
explicit CComGITPtr(DWORD dwCookie) throw();
CComGITPtr(CComGITPtr&& rv);
```

### <a name="parameters"></a>Parametry

*P*<br/>
[w] Wskaźnik interfejsu do przechowywania w globalnej tabeli interfejsu (GIT).

*Git*<br/>
[w] Odwołanie do istniejącego `CComGITPtr` obiektu.

*dwCookie (właśc.*<br/>
[w] Plik cookie służący do identyfikowania wskaźnika interfejsu.

*Rv*<br/>
[w] Obiekt `CComGITPtr` źródłowy do przenoszenia danych z.

### <a name="remarks"></a>Uwagi

Tworzy nowy `CComGITPtr` obiekt, opcjonalnie `CComGITPtr` przy użyciu istniejącego obiektu.

Konstruktor wykorzystujący *rv* jest konstruktorem ruchu. Dane są przenoszone ze źródła, *rv*, a następnie *rv* jest czyszczony.

## <a name="ccomgitptrccomgitptr"></a><a name="dtor"></a>CComGITPtr::~CComGITPtr

Destruktor.

```
~CComGITPtr() throw();
```

### <a name="remarks"></a>Uwagi

Usuwa interfejs z globalnej tabeli interfejsu (GIT), używając [CComGITPtr::Revoke](#revoke).

## <a name="ccomgitptrcopyto"></a><a name="copyto"></a>CComGITPtr::CopyTo

Wywołanie tej metody, aby skopiować interfejs z tabeli interfejsu globalnego (GIT) do przekazanego wskaźnika.

```
HRESULT CopyTo(T** pp) const throw();
```

### <a name="parameters"></a>Parametry

*S*<br/>
Wskaźnik, który ma odbierać interfejs.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Interfejs z GIT jest kopiowany do przekazanego wskaźnika. Wskaźnik musi zostać zwolniony przez wywołującego, gdy nie jest już wymagane.

## <a name="ccomgitptrdetach"></a><a name="detach"></a>CComGITPtr::Detach

Wywołanie tej metody, aby odłączyć `CComGITPtr` interfejs od obiektu.

```
DWORD Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca plik cookie `CComGITPtr` z obiektu.

### <a name="remarks"></a>Uwagi

To do wywołującego, aby usunąć interfejs z GIT, za pomocą [CComGITPtr::Revoke](#revoke).

## <a name="ccomgitptrgetcookie"></a><a name="getcookie"></a>CComGITPtr::GetCookie

Wywołanie tej metody, aby `CComGITPtr` zwrócić plik cookie z obiektu.

```
DWORD GetCookie() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca plik cookie.

### <a name="remarks"></a>Uwagi

Plik cookie jest zmienną używaną do identyfikowania interfejsu i jego lokalizacji.

## <a name="ccomgitptrm_dwcookie"></a><a name="m_dwcookie"></a>CComGITPtr::m_dwCookie

Plik cookie.

```
DWORD m_dwCookie;
```

### <a name="remarks"></a>Uwagi

Plik cookie jest zmienną elementu członkowskiego używaną do identyfikowania interfejsu i jego lokalizacji.

## <a name="ccomgitptroperator-"></a><a name="operator_eq"></a>CComGITPtr::operator =

Operator przypisania.

```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```

### <a name="parameters"></a>Parametry

*P*<br/>
[w] Wskaźnik do interfejsu.

*Git*<br/>
[w] Odwołanie do `CComGITPtr` obiektu.

*dwCookie (właśc.*<br/>
[w] Plik cookie służący do identyfikowania wskaźnika interfejsu.

*Rv*<br/>
[w] Aby `CComGITPtr` przenieść dane z.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CComGITPtr` obiekt.

### <a name="remarks"></a>Uwagi

Przypisuje nową wartość do `CComGITPtr` obiektu z istniejącego obiektu lub z odwołania do tabeli interfejsu globalnego.

## <a name="ccomgitptroperator-dword"></a><a name="operator_dword"></a>CComGITPtr::operator DWORD

Zwraca plik cookie skojarzony z obiektem. `CComGITPtr`

```
operator DWORD() const;
```

### <a name="remarks"></a>Uwagi

Plik cookie jest zmienną używaną do identyfikowania interfejsu i jego lokalizacji.

## <a name="ccomgitptrrevoke"></a><a name="revoke"></a>CComGITPtr::Odwołaj

Wywołanie tej metody, aby usunąć bieżący interfejs z tabeli interfejsu globalnego (GIT).

```
HRESULT Revoke() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Usuwa interfejs z GIT.

## <a name="see-also"></a>Zobacz też

[Free Threaded Marshaler](../../atl/atl-and-the-free-threaded-marshaler.md)<br/>
[Uzyskiwanie dostępu do interfejsów w różnych apartamentach](/windows/win32/com/accessing-interfaces-across-apartments)<br/>
[Kiedy używać tabeli interfejsu globalnego](/windows/win32/com/when-to-use-the-global-interface-table)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
