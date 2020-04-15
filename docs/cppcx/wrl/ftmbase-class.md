---
title: FtmBase — Klasa
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase
- ftm/Microsoft::WRL::FtmBaseCreateGlobalInterfaceTable
- ftm/Microsoft::WRL::FtmBase::DisconnectObject
- ftm/Microsoft::WRL::FtmBase::FtmBase
- ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax
- ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass
- ftm/Microsoft::WRL::FtmBase::MarshalInterface
- ftm/Microsoft::WRL::FtmBase::marshaller_
- ftm/Microsoft::WRL::FtmBase::ReleaseMarshalData
- ftm/Microsoft::WRL::FtmBase::UnmarshalInterface
helpviewer_keywords:
- Microsoft::WRL::FtmBase class
- Microsoft::WRL::FtmBase::CreateGlobalInterfaceTable method
- Microsoft::WRL::FtmBase::DisconnectObject method
- Microsoft::WRL::FtmBase::FtmBase, constructor
- Microsoft::WRL::FtmBase::GetMarshalSizeMax method
- Microsoft::WRL::FtmBase::GetUnmarshalClass method
- Microsoft::WRL::FtmBase::MarshalInterface method
- Microsoft::WRL::FtmBase::marshaller_ data member
- Microsoft::WRL::FtmBase::ReleaseMarshalData method
- Microsoft::WRL::FtmBase::UnmarshalInterface method
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
ms.openlocfilehash: d37cdddda8cf8894016ed80b9055fe106b1600f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371511"
---
# <a name="ftmbase-class"></a>FtmBase — Klasa

Reprezentuje obiekt organizatora bezwątwowego.

## <a name="syntax"></a>Składnia

```cpp
class FtmBase :
    public Microsoft::WRL::Implements<
        Microsoft::WRL::RuntimeClassFlags<WinRtClassicComMix>,
        Microsoft::WRL::CloakedIid<IMarshal>
    >;
```

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Klasa RuntimeClass](runtimeclass-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

| Nazwa                         | Opis                                        |
| ---------------------------- | -------------------------------------------------- |
| [Baza FtmBase::FtmBase](#ftmbase) | Inicjuje nowe wystąpienie klasy `FtmBase`. |

### <a name="public-methods"></a>Metody publiczne

| Nazwa                                                               | Opis                                                                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [FtmBase::CreateGlobalInterfaceTable](#createglobalinterfacetable) | Tworzy globalną tabelę interfejsów (GIT).                                                                                                                              |
| [FtmBase::DisconnectObject](#disconnectobject)                     | Przymusowo zwalnia wszystkie połączenia zewnętrzne do obiektu. Serwer obiektu wywołuje implementację obiektu tej metody przed zamknięciem.                |
| [FtmBase::GetMarshalSizeMax](#getmarshalsizemax)                   | Pobierz górną granicę na liczbę bajtów potrzebnych do organizowania wskaźnika określonego interfejsu na określonym obiekcie.                                                |
| [FtmBase::GetUnmarshalClass](#getunmarshalclass)                   | Pobiera CLSID, który com używa do zlokalizowania biblioteki DLL zawierającej kod dla odpowiedniego serwera proxy. COM ładuje tę bibliotekę DLL, aby utworzyć niezainicjowane wystąpienie serwera proxy. |
| [FtmBase::MarshalInterface](#marshalinterface)                     | Zapisuje w strumieniu dane wymagane do zainicjowania obiektu proxy w niektórych procesach klienta.                                                                          |
| [FtmBase::ReleaseMarshalData](#releasemarshaldata)                 | Niszczy pakiet danych zorganizowanych.                                                                                                                                    |
| [FtmBase::UnmarshalInterface](#unmarshalinterface)                 | Inicjuje nowo utworzony serwer proxy i zwraca wskaźnik interfejsu do tego serwera proxy.                                                                                    |

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

| Nazwa                                | Opis                                       |
| ----------------------------------- | ------------------------------------------------- |
| [Baza FtmBase::marshaller_](#marshaller) | Zawiera odwołanie do bezpłatnego organizatora wątków. |

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`FtmBase`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ftm.h

**Obszar nazw:** Microsoft::WRL

## <a name="ftmbasecreateglobalinterfacetable"></a><a name="createglobalinterfacetable"></a>FtmBase::CreateGlobalInterfaceTable

Tworzy globalną tabelę interfejsów (GIT).

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>Parametry

*Git*<br/>
Po zakończeniu tej operacji wskaźnik do tabeli interfejsu globalnego.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który wskazuje błąd.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej `IGlobalInterfaceTable` informacji, `COM Interfaces` zobacz temat w `COM Reference` podtemat tematu w bibliotece MSDN.

## <a name="ftmbasedisconnectobject"></a><a name="disconnectobject"></a>FtmBase::DisconnectObject

Przymusowo zwalnia wszystkie połączenia zewnętrzne do obiektu. Serwer obiektu wywołuje implementację obiektu tej metody przed zamknięciem.

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>Parametry

*dwReserved (niesłuszne)*<br/>
Zarezerwowane do wykorzystania w przyszłości; musi wynosić zero.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który wskazuje błąd.

## <a name="ftmbaseftmbase"></a><a name="ftmbase"></a>Baza FtmBase::FtmBase

Inicjuje nowe wystąpienie klasy `FtmBase`.

```cpp
FtmBase();
```

## <a name="ftmbasegetmarshalsizemax"></a><a name="getmarshalsizemax"></a>FtmBase::GetMarshalSizeMax

Pobierz górną granicę na liczbę bajtów potrzebnych do organizowania wskaźnika określonego interfejsu na określonym obiekcie.

```cpp
STDMETHODIMP GetMarshalSizeMax(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out DWORD *pSize
) override;
```

### <a name="parameters"></a>Parametry

*Riid*<br/>
Odwołanie do identyfikatora interfejsu, który ma być organizowany.

*Pv*<br/>
Wskaźnik interfejsu do zorganizowania; może mieć wartość NULL.

*dwDestContext (dwDestContext)*<br/>
Kontekst docelowy, w którym określony interfejs ma być nierozsądowany.

Określ jedną lub więcej wartości wyliczenia MSHCTX.

Obecnie odłączanie może wystąpić w innym mieszkaniu bieżącego procesu (MSHCTX_INPROC) lub w innym procesie na tym samym komputerze co bieżący proces (MSHCTX_LOCAL).

*pvDestContext*<br/>
Zarezerwowane do wykorzystania w przyszłości; musi mieć wartość NULL.

*mshlflags ( mshlflags )*<br/>
Flaga wskazująca, czy dane, które mają być organizowane, mają być przesyłane z powrotem do procesu klienta — typowy przypadek — lub zapisywane w tabeli globalnej, gdzie mogą być pobierane przez wielu klientów. Określ jedną lub więcej wartości wyliczenia MSHLFLAGS.

*pSize (rozmiar)*<br/>
Po zakończeniu tej operacji wskaźnik do górnej granicy na ilość danych, które mają być zapisywane do strumienia kierowaniu.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie E_FAIL lub E_NOINTERFACE.

## <a name="ftmbasegetunmarshalclass"></a><a name="getunmarshalclass"></a>FtmBase::GetUnmarshalClass

Pobiera CLSID, który com używa do zlokalizowania biblioteki DLL zawierającej kod dla odpowiedniego serwera proxy. COM ładuje tę bibliotekę DLL, aby utworzyć niezainicjowane wystąpienie serwera proxy.

```cpp
STDMETHODIMP GetUnmarshalClass(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out CLSID *pCid
) override;
```

### <a name="parameters"></a>Parametry

*Riid*<br/>
Odwołanie do identyfikatora interfejsu, który ma być organizowany.

*Pv*<br/>
Wskaźnik do interfejsu, który ma być organizowany; może być null, jeśli wywołujący nie ma wskaźnika do żądanego interfejsu.

*dwDestContext (dwDestContext)*<br/>
Kontekst docelowy, w którym określony interfejs ma być nierozsądowany.

Określ jedną lub więcej wartości wyliczenia MSHCTX.

Rozpakczenie może wystąpić w innym mieszkaniu bieżącego procesu (MSHCTX_INPROC) lub w innym procesie na tym samym komputerze co bieżący proces (MSHCTX_LOCAL).

*pvDestContext*<br/>
Zarezerwowane do wykorzystania w przyszłości; musi mieć wartość NULL.

*mshlflags ( mshlflags )*<br/>
Po zakończeniu tej operacji wskaźnik do identyfikatora CLSID, który ma być używany do tworzenia serwera proxy w procesie klienta.

*Pcid*

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie S_FALSE.

## <a name="ftmbasemarshalinterface"></a><a name="marshalinterface"></a>FtmBase::MarshalInterface

Zapisuje w strumieniu dane wymagane do zainicjowania obiektu proxy w niektórych procesach klienta.

```cpp
STDMETHODIMP MarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags
) override;
```

### <a name="parameters"></a>Parametry

*pStm (pStm)*<br/>
Wskaźnik do strumienia, który ma być używany podczas organizowania.

*Riid*<br/>
Odwołanie do identyfikatora interfejsu, który ma być organizowany. Ten interfejs musi pochodzić `IUnknown` z interfejsu.

*Pv*<br/>
Wskaźnik do wskaźnika interfejsu, który ma być organizowany; może być null, jeśli wywołujący nie ma wskaźnika do żądanego interfejsu.

*dwDestContext (dwDestContext)*<br/>
Kontekst docelowy, w którym określony interfejs ma być nierozsądowany.

Określ jedną lub więcej wartości wyliczenia MSHCTX.

Rozpakczenie może wystąpić w innym mieszkaniu bieżącego procesu (MSHCTX_INPROC) lub w innym procesie na tym samym komputerze co bieżący proces (MSHCTX_LOCAL).

*pvDestContext*<br/>
Zarezerwowane do wykorzystania w przyszłości; musi wynosić zero.

*mshlflags ( mshlflags )*<br/>
Określa, czy dane, które mają być organizowane mają być przesyłane z powrotem do procesu klienta — typowy przypadek — lub zapisywane w tabeli globalnej, gdzie mogą być pobierane przez wielu klientów.

### <a name="return-value"></a>Wartość zwracana

S_OK Wskaźnik interfejsu został pomyślnie zorganizowany.

E_NOINTERFACE Określony interfejs nie jest obsługiwany.

STG_E_MEDIUMFULL Strumień jest pełny.

E_FAIL Operacja nie powiodła się.

## <a name="ftmbasemarshaller_"></a><a name="marshaller"></a>Baza FtmBase::marshaller_

Zawiera odwołanie do bezpłatnego organizatora wątków.

```cpp
Microsoft::WRL::ComPtr<IMarshal> marshaller_; ;
```

## <a name="ftmbasereleasemarshaldata"></a><a name="releasemarshaldata"></a>FtmBase::ReleaseMarshalData

Niszczy pakiet danych zorganizowanych.

```cpp
STDMETHODIMP ReleaseMarshalData(
   __in IStream *pStm
) override;
```

### <a name="parameters"></a>Parametry

*pStm (pStm)*<br/>
Wskaźnik do strumienia, który zawiera pakiet danych do zniszczenia.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który wskazuje błąd.

## <a name="ftmbaseunmarshalinterface"></a><a name="unmarshalinterface"></a>FtmBase::UnmarshalInterface

Inicjuje nowo utworzony serwer proxy i zwraca wskaźnik interfejsu do tego serwera proxy.

```cpp
STDMETHODIMP UnmarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __deref_out void **ppv
) override;
```

### <a name="parameters"></a>Parametry

*pStm (pStm)*<br/>
Wskaźnik do strumienia, z którego wskaźnik interfejsu ma być unmarshaled.

*Riid*<br/>
Odwołanie do identyfikatora interfejsu, który ma być niemarshalowany.

*Ppv*<br/>
Po zakończeniu tej operacji adres zmiennej wskaźnika, która odbiera wskaźnik interfejsu żądany w *riid*. Jeśli ta operacja zakończy się pomyślnie, **ppv* zawiera żądany wskaźnik interfejsu interfejsu, który ma być unmarshaled.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w inny sposób E_NOINTERFACE lub E_FAIL.
