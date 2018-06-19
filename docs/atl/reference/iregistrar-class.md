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
ms.openlocfilehash: 89d1e9269536ee28f2c8dd29819ff594c89c186b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363754"
---
# <a name="iregistrar-interface"></a>Interfejs IRegistrar
Ten interfejs jest zdefiniowany w atliface.h i jest używana wewnętrznie przez funkcje Członkowskie CAtlModule takich jak [UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced).   
  
## <a name="syntax"></a>Składnia  
  
```
typedef interface IRegistrar IRegistrar;
```  
## <a name="remarks"></a>Uwagi
Zobacz temat [przy użyciu parametry wymienne (Rejestrator preprocesora)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) więcej szczegółów.  

## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IRegistrar::ResourceRegisterSz](#resourceregistersz)|Rejestruje zasobu. |  
|[IRegistrar::ResourceUnregisterSz](#resourceunregistersz)| Wyrejestrowuje zasobu.|  
|[IRegistrar::FileRegister](#fileregister)|Rejestruje plik.|  
|[IRegistrar::FileUnregister](#fileunregister)|Wyrejestrowuje pliku.|  
|[IRegistrar::StringRegister](#stringregister)|Rejestruje ciąg.|  
|[IRegistrar::StringUnregister](#stringunregister)|Wyrejestrowuje ciąg|  
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
    */ _In_z_ LPCOLESTR fileName) = 0;
```  
  
 
##  <a name="stringregister"></a>  IRegistrar::StringRegister  
  Rejestruje dane określonego ciągu.
```
virtual HRESULT STDMETHODCALLTYPE StringRegister( 
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```  
  
##  <a name="stringunregister"></a>  IRegistrar::StringUnregister
 Wyrejestrowuje danych określonego ciągu.  
  
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
 [Używanie wymiennych parametrów (preprocesor rejestratora)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)  
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasy modułów](../../atl/atl-module-classes.md)   
 [Składnik rejestru (Rejestrator)](../../atl/atl-registry-component-registrar.md)  
