---
title: Interfejs IRegistrar | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2/1/2017
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- Iregistrar Interface
ms.assetid: e88c04b7-0c93-4ae8-aeb9-ecd78f87421e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 10e5a6fda373c79b85dac5cfcf19739276a5c12f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039520"
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

## <a name="see-also"></a>Zobacz też

[Używanie wymiennych parametrów (preprocesor rejestratora)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)<br/>
[Składnik rejestru (Rejestrator)](../../atl/atl-registry-component-registrar.md)
