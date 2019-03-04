---
title: Interfejs IRegistrar
ms.date: 2/1/2017
f1_keywords:
- IRegistrar
- ATLIFASE/ATL::IRegistrar
- ATLIFASE/ATL::IRegistrar::ResourceRegisterSz
- ATLIFASE/ATL::IRegistrar::ResourceUnregisterSz
- ATLIFASE/ATL::IRegistrar::FileRegister
- ATLIFASE/ATL::IRegistrar::FileUnregister
- ATLIFASE/ATL::IRegistrar::StringRegister
- ATLIFASE/ATL::IRegistrar::StringUnregister
- ATLIFASE/ATL::IRegistrar::ResourceRegister
- ATLIFASE/ATL::IRegistrar::ResourceUnregister
helpviewer_keywords:
- Iregistrar Interface
ms.assetid: e88c04b7-0c93-4ae8-aeb9-ecd78f87421e
ms.openlocfilehash: 984d95a1e0adb6835db7ca4bcabcff21f0be7beb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281320"
---
# <a name="iregistrar-interface"></a>Interfejs IRegistrar

Ten interfejs jest zdefiniowany w atliface.h i jest używana wewnętrznie przez funkcje składowe CAtlModule takich jak [UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced).

## <a name="syntax"></a>Składnia

```
typedef interface IRegistrar IRegistrar;
```

## <a name="remarks"></a>Uwagi

Zobacz temat [przy użyciu zastępowalnych parametrów (Preprocesor rejestratora)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) Aby uzyskać więcej informacji.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IRegistrar::ResourceRegisterSz](#resourceregistersz)|Rejestruje zasobu. |
|[IRegistrar::ResourceUnregisterSz](#resourceunregistersz)| Wyrejestrowuje zasobu.|
|[IRegistrar::FileRegister](#fileregister)|Rejestruje plik.|
|[IRegistrar::FileUnregister](#fileunregister)|Wyrejestrowuje pliku.|
|[IRegistrar::StringRegister](#stringregister)|Rejestruje ciąg.|
|[IRegistrar::StringUnregister](#stringunregister)|Wyrejestrowuje ciągu|
|[IRegistrar::ResourceRegister](#resourceregister)|Rejestruje zasobu.|
|[IRegistrar::ResourceUnregister](#resourceunregister)|Wyrejestrowuje zasobu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlifase.h

##  <a name="resourceregistersz"></a>  IRegistrar::ResourceRegisterSz

Rejestruje zasobu.

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

##  <a name="resourceunregistersz"></a>  IRegistrar::ResourceUnregisterSz

Wyrejestrowuje zasobu.

```
virtual HRESULT STDMETHODCALLTYPE ResourceUnregisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

##  <a name="fileregister"></a>  IRegistrar::FileRegister

Rejestruje plik.

```
virtual HRESULT STDMETHODCALLTYPE FileRegister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

##  <a name="fileunregister"></a>  IRegistrar::FileUnregister

Wyrejestrowuje pliku.

```
virtual HRESULT STDMETHODCALLTYPE FileUnregister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

##  <a name="stringregister"></a>  IRegistrar::StringRegister

Rejestruje dane określonego ciągu.

```
virtual HRESULT STDMETHODCALLTYPE StringRegister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

##  <a name="stringunregister"></a>  IRegistrar::StringUnregister

Wyrejestrowuje dane określonego ciągu.

```
virtualHRESULT STDMETHODCALLTYPE StringUnregister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

##  <a name="resourceregister"></a>  IRegistrar::ResourceRegister

Rejestruje zasobu.

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

##  <a name="resourceunregister"></a>  IRegistrar::ResourceUnregister

Wyrejestrowuje zasobu.

```
virtualHRESULT STDMETHODCALLTYPE ResourceUnregister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="see-also"></a>Zobacz także

[Używanie wymiennych parametrów (preprocesor rejestratora)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)<br/>
[Składnik rejestru (Rejestrator)](../../atl/atl-registry-component-registrar.md)
