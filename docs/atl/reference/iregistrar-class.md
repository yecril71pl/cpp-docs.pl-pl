---
title: Interfejs IRegistrar
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
ms.openlocfilehash: 98943fe294322715723bd91207a6f3320ca1ffb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329462"
---
# <a name="iregistrar-interface"></a>Interfejs IRegistrar

Ten interfejs jest zdefiniowany w pliku atliface.h i jest używany wewnętrznie przez funkcje członkowskie CAtlModule, takie jak [UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced).

## <a name="syntax"></a>Składnia

```
typedef interface IRegistrar IRegistrar;
```

## <a name="remarks"></a>Uwagi

Więcej informacji można znaleźć w temacie [Korzystanie z parametrów wymiennych (preprocesor rejestratora).](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IRegistrar::ResourceRegisterSz](#resourceregistersz)|Rejestruje zasób. |
|[IRegistrar::ResourceUnregisterSz](#resourceunregistersz)| Wyrejestrowyje zasób.|
|[IRegistrar::FileRegister](#fileregister)|Rejestruje plik.|
|[IRegistrar::FileUnregister](#fileunregister)|Wyrejestruje plik.|
|[IRegistrar::StringRegister](#stringregister)|Rejestruje ciąg.|
|[IRegistrar::StringUnregister](#stringunregister)|Wyrejestrowyje ciąg|
|[IRegistrar::Zarejestruj rejestr zasobów](#resourceregister)|Rejestruje zasób.|
|[IRegistrar::ResourceUnregister](#resourceunregister)|Wyrejestrowyje zasób.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlifase.h

## <a name="iregistrarresourceregistersz"></a><a name="resourceregistersz"></a>IRegistrar::ResourceRegisterSz

Rejestruje zasób.

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarresourceunregistersz"></a><a name="resourceunregistersz"></a>IRegistrar::ResourceUnregisterSz

Wyrejestrowyje zasób.

```
virtual HRESULT STDMETHODCALLTYPE ResourceUnregisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarfileregister"></a><a name="fileregister"></a>IRegistrar::FileRegister

Rejestruje plik.

```
virtual HRESULT STDMETHODCALLTYPE FileRegister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

## <a name="iregistrarfileunregister"></a><a name="fileunregister"></a>IRegistrar::FileUnregister

Wyrejestruje plik.

```
virtual HRESULT STDMETHODCALLTYPE FileUnregister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

## <a name="iregistrarstringregister"></a><a name="stringregister"></a>IRegistrar::StringRegister

Rejestruje określone dane ciągu.

```
virtual HRESULT STDMETHODCALLTYPE StringRegister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

## <a name="iregistrarstringunregister"></a><a name="stringunregister"></a>IRegistrar::StringUnregister

Wyrejestruje określone dane ciągu.

```
virtualHRESULT STDMETHODCALLTYPE StringUnregister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

## <a name="iregistrarresourceregister"></a><a name="resourceregister"></a>IRegistrar::Zarejestruj rejestr zasobów

Rejestruje zasób.

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarresourceunregister"></a><a name="resourceunregister"></a>IRegistrar::ResourceUnregister

Wyrejestrowyje zasób.

```
virtualHRESULT STDMETHODCALLTYPE ResourceUnregister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="see-also"></a>Zobacz też

[Korzystanie z wymiennych parametrów (preprocesor rejestratora)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)<br/>
[Składnik rejestru (rejestrator)](../../atl/atl-registry-component-registrar.md)
