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
ms.openlocfilehash: b28b7ee0038e4f828f43fcc3f0d49a2d9e092315
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844044"
---
# <a name="ftmbase-class"></a>FtmBase — Klasa

Reprezentuje obiekt organizatora wolnego wątku.

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
| [FtmBase:: FtmBase](#ftmbase) | Inicjuje nowe wystąpienie klasy `FtmBase`. |

### <a name="public-methods"></a>Metody publiczne

| Nazwa                                                               | Opis                                                                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [FtmBase:: CreateGlobalInterfaceTable —](#createglobalinterfacetable) | Tworzy globalną tabelę interfejsów (GIT).                                                                                                                              |
| [FtmBase::D isconnectobject](#disconnectobject)                     | Wymuszanie zwolnienia wszystkich połączeń zewnętrznych do obiektu. Serwer obiektu wywołuje implementację tej metody obiektu przed zamknięciem.                |
| [FtmBase:: GetMarshalSizeMax —](#getmarshalsizemax)                   | Pobierz górną granicę dla liczby bajtów wymaganych do skierowania określonego wskaźnika interfejsu do określonego obiektu.                                                |
| [FtmBase:: GetUnmarshalClass —](#getunmarshalclass)                   | Pobiera identyfikator CLSID używany przez COM do lokalizowania biblioteki DLL zawierającej kod dla odpowiedniego serwera proxy. COM ładuje tę bibliotekę DLL w celu utworzenia niezainicjowanego wystąpienia serwera proxy. |
| [FtmBase:: MarshalInterface —](#marshalinterface)                     | Zapisuje w strumieniu dane wymagane do zainicjowania obiektu serwera proxy w pewnym procesie klienta.                                                                          |
| [FtmBase:: ReleaseMarshalData —](#releasemarshaldata)                 | Niszczy pakiet danych zorganizowanych.                                                                                                                                    |
| [FtmBase:: UnmarshalInterface —](#unmarshalinterface)                 | Inicjuje nowo utworzony serwer proxy i zwraca wskaźnik interfejsu do tego serwera proxy.                                                                                    |

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

| Nazwa                                | Opis                                       |
| ----------------------------------- | ------------------------------------------------- |
| [FtmBase:: marshaller_](#marshaller) | Przechowuje odwołanie do organizatora trybu wolnych wątków. |

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`FtmBase`

## <a name="requirements"></a>Wymagania

**Nagłówek:** FTM. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="ftmbasecreateglobalinterfacetable"></a><a name="createglobalinterfacetable"></a> FtmBase:: CreateGlobalInterfaceTable —

Tworzy globalną tabelę interfejsów (GIT).

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>Parametry

*narzędzia*<br/>
Po zakończeniu tej operacji wskaźnik do tabeli interfejsu globalnego.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie wynik HRESULT wskazuje na błąd.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [`IGlobalInterfaceTable`](/windows/win32/api/objidl/nn-objidl-iglobalinterfacetable).

## <a name="ftmbasedisconnectobject"></a><a name="disconnectobject"></a> FtmBase::D isconnectobject

Wymuszanie zwolnienia wszystkich połączeń zewnętrznych do obiektu. Serwer obiektu wywołuje implementację tej metody obiektu przed zamknięciem.

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>Parametry

*dwReserved*<br/>
Zarezerwowane do użytku w przyszłości; musi być równa zero.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie wynik HRESULT wskazuje na błąd.

## <a name="ftmbaseftmbase"></a><a name="ftmbase"></a> FtmBase:: FtmBase

Inicjuje nowe wystąpienie klasy `FtmBase`.

```cpp
FtmBase();
```

## <a name="ftmbasegetmarshalsizemax"></a><a name="getmarshalsizemax"></a> FtmBase:: GetMarshalSizeMax —

Pobierz górną granicę dla liczby bajtów wymaganych do skierowania określonego wskaźnika interfejsu do określonego obiektu.

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

*riid*<br/>
Odwołanie do identyfikatora interfejsu, który ma być zorganizowany.

*wa*<br/>
Wskaźnik interfejsu, który ma być zorganizowany; może mieć wartość NULL.

*dwDestContext*<br/>
Kontekst docelowy, w którym określony interfejs ma być nieorganizowany.

Określ co najmniej jedną wartość wyliczenia MSHCTX.

Obecnie rozorganizowanie może odbywać się w innej komórkowym procesie (MSHCTX_INPROC) lub w innym procesie na tym samym komputerze, na którym jest obecny proces (MSHCTX_LOCAL).

*pvDestContext*<br/>
Zarezerwowane do użytku w przyszłości; musi mieć wartość NULL.

*mshlflags*<br/>
Flaga oznaczająca, czy dane, które mają być organizowane, są przesyłane z powrotem do procesu klienta — typowego przypadku — lub zapisywane w tabeli globalnej, skąd mogą być pobierane przez wielu klientów. Określ co najmniej jedną wartość wyliczenia MSHLFLAGS.

*pSize*<br/>
Po zakończeniu tej operacji, wskaźnik do górnej granicy ilości danych, które mają być zapisywane w strumieniu organizowania.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie E_FAIL lub E_NOINTERFACE.

## <a name="ftmbasegetunmarshalclass"></a><a name="getunmarshalclass"></a> FtmBase:: GetUnmarshalClass —

Pobiera identyfikator CLSID używany przez COM do lokalizowania biblioteki DLL zawierającej kod dla odpowiedniego serwera proxy. COM ładuje tę bibliotekę DLL w celu utworzenia niezainicjowanego wystąpienia serwera proxy.

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

*riid*<br/>
Odwołanie do identyfikatora interfejsu, który ma być zorganizowany.

*wa*<br/>
Wskaźnik do interfejsu, który ma być zorganizowany; może mieć wartość NULL, jeśli obiekt wywołujący nie ma wskaźnika do żądanego interfejsu.

*dwDestContext*<br/>
Kontekst docelowy, w którym określony interfejs ma być nieorganizowany.

Określ co najmniej jedną wartość wyliczenia MSHCTX.

Cofanie organizowania może wystąpić w innej komórkowym procesie (MSHCTX_INPROC) lub w innym procesie na tym samym komputerze, na którym jest obecny proces (MSHCTX_LOCAL).

*pvDestContext*<br/>
Zarezerwowane do użytku w przyszłości; musi mieć wartość NULL.

*mshlflags*<br/>
Po zakończeniu tej operacji należy wskaźnikiem do identyfikatora CLSID, który ma być używany do tworzenia serwera proxy w procesie klienta.

*pCid*

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie S_FALSE.

## <a name="ftmbasemarshalinterface"></a><a name="marshalinterface"></a> FtmBase:: MarshalInterface —

Zapisuje w strumieniu dane wymagane do zainicjowania obiektu serwera proxy w pewnym procesie klienta.

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

*pStm*<br/>
Wskaźnik do strumienia, który ma być używany podczas organizowania.

*riid*<br/>
Odwołanie do identyfikatora interfejsu, który ma być zorganizowany. Ten interfejs musi być pochodny `IUnknown` interfejsu.

*wa*<br/>
Wskaźnik na wskaźnik interfejsu, który ma być zorganizowany; może mieć wartość NULL, jeśli obiekt wywołujący nie ma wskaźnika do żądanego interfejsu.

*dwDestContext*<br/>
Kontekst docelowy, w którym określony interfejs ma być nieorganizowany.

Określ co najmniej jedną wartość wyliczenia MSHCTX.

Proces cofania organizowania może wystąpić w innej komórkowym procesie (MSHCTX_INPROC) lub w innym procesie na tym samym komputerze, na którym jest obecny proces (MSHCTX_LOCAL).

*pvDestContext*<br/>
Zarezerwowane do użytku w przyszłości; musi być równa zero.

*mshlflags*<br/>
Określa, czy dane, które mają być organizowane, mają być przesyłane z powrotem do procesu klienta — typowym przypadkiem — czy też zapisywane w tabeli globalnej, skąd mogą być pobierane przez wielu klientów.

### <a name="return-value"></a>Wartość zwracana

S_OK pomyślnie zorganizowany wskaźnik interfejsu.

E_NOINTERFACE określony interfejs nie jest obsługiwany.

STG_E_MEDIUMFULL strumień jest zapełniony.

E_FAIL operacji nie powiodła się.

## <a name="ftmbasemarshaller_"></a><a name="marshaller"></a> FtmBase:: marshaller_

Przechowuje odwołanie do organizatora trybu wolnych wątków.

```cpp
Microsoft::WRL::ComPtr<IMarshal> marshaller_; ;
```

## <a name="ftmbasereleasemarshaldata"></a><a name="releasemarshaldata"></a> FtmBase:: ReleaseMarshalData —

Niszczy pakiet danych zorganizowanych.

```cpp
STDMETHODIMP ReleaseMarshalData(
   __in IStream *pStm
) override;
```

### <a name="parameters"></a>Parametry

*pStm*<br/>
Wskaźnik do strumienia zawierającego pakiet danych, który ma zostać zniszczony.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie wynik HRESULT wskazuje na błąd.

## <a name="ftmbaseunmarshalinterface"></a><a name="unmarshalinterface"></a> FtmBase:: UnmarshalInterface —

Inicjuje nowo utworzony serwer proxy i zwraca wskaźnik interfejsu do tego serwera proxy.

```cpp
STDMETHODIMP UnmarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __deref_out void **ppv
) override;
```

### <a name="parameters"></a>Parametry

*pStm*<br/>
Wskaźnik do strumienia, z którego ma zostać odorganizowany wskaźnik interfejsu.

*riid*<br/>
Odwołanie do identyfikatora interfejsu, który ma zostać odorganizowany.

*ppv*<br/>
Po zakończeniu tej operacji adres zmiennej wskaźnika, który odbiera wskaźnik interfejsu żądany w *riid*. Jeśli ta operacja zakończyła się pomyślnie, **PPV* zawiera żądany wskaźnik interfejsu, który ma zostać odorganizowany.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie E_NOINTERFACE lub E_FAIL.
