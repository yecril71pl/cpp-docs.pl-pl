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
ms.openlocfilehash: fb7f103d8ea647f554d9bbf26c2e218d34f6b1ff
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58787483"
---
# <a name="ftmbase-class"></a>FtmBase — Klasa

Reprezentuje obiekt bezwątkowego.

## <a name="syntax"></a>Składnia

```cpp
class FtmBase :
    public Microsoft::WRL::Implements<
        Microsoft::WRL::RuntimeClassFlags<WinRtClassicComMix>,
        Microsoft::WRL::CloakedIid<IMarshal>
    >;
```

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [runtimeclass — klasa](runtimeclass-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

| Nazwa                         | Opis                                        |
| ---------------------------- | -------------------------------------------------- |
| [FtmBase::FtmBase](#ftmbase) | Inicjuje nowe wystąpienie klasy `FtmBase` klasy. |

### <a name="public-methods"></a>Metody publiczne

| Nazwa                                                               | Opis                                                                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [FtmBase::CreateGlobalInterfaceTable](#createglobalinterfacetable) | Tworzy tabelę interfejsu globalnego (GIT).                                                                                                                              |
| [FtmBase::DisconnectObject](#disconnectobject)                     | Wymuś zwalnia wszystkie połączenia zewnętrzne do obiektu. Serwer obiektu wywołuje obiekt implementacja tej metody przed zamykanie.                |
| [FtmBase::GetMarshalSizeMax](#getmarshalsizemax)                   | Uzyskaj górnej granicy liczby bajtów potrzebnych do organizowania określony wskaźnik interfejsu do określonego obiektu.                                                |
| [FtmBase::GetUnmarshalClass](#getunmarshalclass)                   | Pobiera identyfikator klasy, który używa modelu COM, aby zlokalizować bibliotekę DLL zawierającego kod dla odpowiedniego serwera proxy. COM ładuje tę bibliotekę DLL, aby utworzyć wystąpienie niezainicjowanej serwera proxy. |
| [FtmBase::MarshalInterface](#marshalinterface)                     | Zapisuje w strumieniu danych wymagane do zainicjowania obiektu serwera proxy, w niektórych procesu klienta.                                                                          |
| [FtmBase::ReleaseMarshalData](#releasemarshaldata)                 | Niszczy pakietów danych zorganizowanej.                                                                                                                                    |
| [FtmBase::UnmarshalInterface](#unmarshalinterface)                 | Inicjuje nowo utworzony serwer proxy i zwraca wskaźnik interfejsu do tego serwera proxy.                                                                                    |

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

| Nazwa                                | Opis                                       |
| ----------------------------------- | ------------------------------------------------- |
| [FtmBase::marshaller_](#marshaller) | Zawiera odwołanie do marshaler trybu. |

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`FtmBase`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ftm.h

**Namespace:** Microsoft::WRL

## <a name="createglobalinterfacetable"></a>FtmBase::CreateGlobalInterfaceTable

Tworzy tabelę interfejsu globalnego (GIT).

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>Parametry

*git*<br/>
Gdy ta operacja zostanie ukończone, wskaźnik tabeli interfejsu globalnego.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz `IGlobalInterfaceTable` tematu w `COM Interfaces` podrzędny z `COM Reference` w bibliotece MSDN.

## <a name="disconnectobject"></a>FtmBase::DisconnectObject

Wymuś zwalnia wszystkie połączenia zewnętrzne do obiektu. Serwer obiektu wywołuje obiekt implementacja tej metody przed zamykanie.

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>Parametry

*dwReserved*<br/>
Zarezerwowane dla przyszłego użytku; musi mieć wartość zero.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="ftmbase"></a>FtmBase::FtmBase

Inicjuje nowe wystąpienie klasy `FtmBase` klasy.

```cpp
FtmBase();
```

## <a name="getmarshalsizemax"></a>FtmBase::GetMarshalSizeMax

Uzyskaj górnej granicy liczby bajtów potrzebnych do organizowania określony wskaźnik interfejsu do określonego obiektu.

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

*Parametr riid*<br/>
Odwołanie do identyfikatora interfejsu aby być organizowany.

*Wa*<br/>
Wskaźnik interfejsu do przekazywania; może mieć wartości NULL.

*dwDestContext*<br/>
Miejsce docelowe kontekst, w którym ma zostać wycofana określonego interfejsu.

Określ co najmniej jednej wartości wyliczenia MSHCTX.

Obecnie unmarshaling może wystąpić w innym apartamentu bieżącego procesu (MSHCTX_INPROC) lub w inny proces na tym samym komputerze, co bieżący proces (MSHCTX_LOCAL).

*pvDestContext*<br/>
Zarezerwowane dla przyszłego użytku; musi mieć wartość NULL.

*mshlflags*<br/>
Flaga wskazująca, czy ma być przesyłane z powrotem do procesu klienta dane, które mają być przekazywane — typowy przypadek — lub zapisywane w tabeli globalne, gdzie mogą być pobierane przez wielu klientów. Określ co najmniej jednej wartości wyliczenia MSHLFLAGS.

*pSize*<br/>
Gdy ta operacja zostanie ukończone, wskaźnik do górnej granicy ilości danych do zapisania do organizowania strumienia.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie, lub E_NOINTERFACE E_FAIL.

## <a name="getunmarshalclass"></a>FtmBase::GetUnmarshalClass

Pobiera identyfikator klasy, który używa modelu COM, aby zlokalizować bibliotekę DLL zawierającego kod dla odpowiedniego serwera proxy. COM ładuje tę bibliotekę DLL, aby utworzyć wystąpienie niezainicjowanej serwera proxy.

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

*Parametr riid*<br/>
Odwołanie do identyfikatora interfejsu aby być organizowany.

*Wa*<br/>
Wskaźnik do interfejsu, aby zorganizować; może mieć wartości NULL, jeśli obiekt wywołujący nie ma wskaźnik do żądanego interfejsu.

*dwDestContext*<br/>
Miejsce docelowe kontekst, w którym ma zostać wycofana określonego interfejsu.

Określ co najmniej jednej wartości wyliczenia MSHCTX.

Unmarshaling może wystąpić w innym apartamentu bieżącego procesu (MSHCTX_INPROC) lub w inny proces na tym samym komputerze, co bieżący proces (MSHCTX_LOCAL).

*pvDestContext*<br/>
Zarezerwowane dla przyszłego użytku; musi mieć wartość NULL.

*mshlflags*<br/>
Gdy ta operacja zostanie ukończone, wskaźnik do CLSID, który ma być używany do tworzenia serwera proxy w procesie klienta.

*pCid*

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość S_FALSE.

## <a name="marshalinterface"></a>FtmBase::MarshalInterface

Zapisuje w strumieniu danych wymagane do zainicjowania obiektu serwera proxy, w niektórych procesu klienta.

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
Wskaźnik do strumienia, który ma być używany podczas kierowania.

*Parametr riid*<br/>
Odwołanie do identyfikatora interfejsu aby być organizowany. Ten interfejs musi pochodzić od `IUnknown` interfejsu.

*Wa*<br/>
Wskaźnik do wskaźnika interfejsu, aby zorganizować; może mieć wartości NULL, jeśli obiekt wywołujący nie ma wskaźnik do żądanego interfejsu.

*dwDestContext*<br/>
Miejsce docelowe kontekst, w którym ma zostać wycofana określonego interfejsu.

Określ co najmniej jednej wartości wyliczenia MSHCTX.

Unmarshaling może wystąpić w innym apartamentu bieżącego procesu (MSHCTX_INPROC) lub inny proces na tym samym komputerze, co bieżący proces (MSHCTX_LOCAL).

*pvDestContext*<br/>
Zarezerwowane dla przyszłego użytku; musi mieć wartość zero.

*mshlflags*<br/>
Określa, czy dane, które mają być przekazywane do być przesyłane z powrotem do procesu klienta — typowy przypadek — lub zapisywane w tabeli globalne, gdzie mogą być pobierane przez wielu klientów.

### <a name="return-value"></a>Wartość zwracana

S_OK wskaźnika interfejsu zorganizować został pomyślnie.

E_NOINTERFACE określonego interfejsu nie jest obsługiwane.

STG_E_MEDIUMFULL strumień jest pełny.

E_FAIL operacja nie powiodła się.

## <a name="marshaller"></a>FtmBase::marshaller_

Zawiera odwołanie do marshaler trybu.

```cpp
Microsoft::WRL::ComPtr<IMarshal> marshaller_; ;
```

## <a name="releasemarshaldata"></a>FtmBase::ReleaseMarshalData

Niszczy pakietów danych zorganizowanej.

```cpp
STDMETHODIMP ReleaseMarshalData(
   __in IStream *pStm
) override;
```

### <a name="parameters"></a>Parametry

*pStm*<br/>
Wskaźnik do strumienia, który zawiera pakiet danych, które mają zostać zniszczone.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="unmarshalinterface"></a>FtmBase::UnmarshalInterface

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
Wskaźnik do strumienia, z którego ma zostać wycofana wskaźnika interfejsu.

*Parametr riid*<br/>
Odwołanie do identyfikatora interfejsu Aby zostać wycofana.

*ppv*<br/>
Po zakończeniu tej operacji, adres zmiennej wskaźnika, który otrzymuje wskaźnik interfejsu w *riid*. Jeśli operacja zakończy się powodzeniem, **ppv* znajduje się wskaźnik interfejsu żądanego interfejsu Aby zostać wycofana.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie E_NOINTERFACE lub E_FAIL.
