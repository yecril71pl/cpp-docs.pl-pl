---
title: IRegistrar, interfejs
ms.date: 02/01/2017
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
ms.openlocfilehash: e347bdba1656a53cd705123a26650dad50d3892f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417615"
---
# <a name="iregistrar-interface"></a>IRegistrar, interfejs

Ten interfejs jest zdefiniowany w atliface. h i jest używany wewnętrznie przez CAtlModule funkcje członkowskie, takie jak [UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced).

## <a name="syntax"></a>Składnia

```
typedef interface IRegistrar IRegistrar;
```

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz temat [Używanie parametrów wymiennych (preprocesora rejestratora)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) .

## <a name="members"></a>Members

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[IRegistrar::ResourceRegisterSz](#resourceregistersz)|Rejestruje zasób. |
|[IRegistrar::ResourceUnregisterSz](#resourceunregistersz)| Wyrejestrowuje zasób.|
|[IRegistrar::FileRegister](#fileregister)|Rejestruje plik.|
|[IRegistrar::FileUnregister](#fileunregister)|Wyrejestrowuje plik.|
|[IRegistrar::StringRegister](#stringregister)|Rejestruje ciąg.|
|[IRegistrar::StringUnregister](#stringunregister)|Wyrejestrowuje ciąg|
|[IRegistrar::ResourceRegister](#resourceregister)|Rejestruje zasób.|
|[IRegistrar::ResourceUnregister](#resourceunregister)|Wyrejestrowuje zasób.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlifase. h

##  <a name="resourceregistersz"></a>IRegistrar::ResourceRegisterSz

Rejestruje zasób.

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

##  <a name="resourceunregistersz"></a>IRegistrar::ResourceUnregisterSz

Wyrejestrowuje zasób.

```
virtual HRESULT STDMETHODCALLTYPE ResourceUnregisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

##  <a name="fileregister"></a>IRegistrar::FileRegister

Rejestruje plik.

```
virtual HRESULT STDMETHODCALLTYPE FileRegister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

##  <a name="fileunregister"></a>IRegistrar::FileUnregister

Wyrejestrowuje plik.

```
virtual HRESULT STDMETHODCALLTYPE FileUnregister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

##  <a name="stringregister"></a>IRegistrar::StringRegister

Rejestruje określone dane ciągu.

```
virtual HRESULT STDMETHODCALLTYPE StringRegister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

##  <a name="stringunregister"></a>IRegistrar::StringUnregister

Wyrejestrowuje określone dane ciągu.

```
virtualHRESULT STDMETHODCALLTYPE StringUnregister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

##  <a name="resourceregister"></a>IRegistrar::ResourceRegister

Rejestruje zasób.

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

##  <a name="resourceunregister"></a>IRegistrar::ResourceUnregister

Wyrejestrowuje zasób.

```
virtualHRESULT STDMETHODCALLTYPE ResourceUnregister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="see-also"></a>Zobacz też

[Używanie wymiennych parametrów (preprocesor rejestratora)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)<br/>
[Składnik rejestru (Rejestrator)](../../atl/atl-registry-component-registrar.md)
