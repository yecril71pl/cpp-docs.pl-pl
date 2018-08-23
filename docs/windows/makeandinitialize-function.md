---
title: MakeAndInitialize, funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAndInitialize
dev_langs:
- C++
ms.assetid: 71ceeb12-d2a2-4317-b010-3dcde1b39467
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 196834a5181164d141c1b9ee025cee5b6f1a5bd9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591049"
---
# <a name="makeandinitialize-function"></a>MakeAndInitialize — Funkcja

Inicjuje określonej klasy środowiska wykonawczego Windows. Ta funkcja służy do utworzenia wystąpienia składnika, który jest zdefiniowany w tym samym module.

## <a name="syntax"></a>Składnia

```cpp
template <typename T, typename I,
typename TArg1,
typename TArg2,
typename TArg3,
typename TArg4,
typename TArg5,
typename TArg6,
typename TArg7,
typename TArg8,
typename TArg9> HRESULT MakeAndInitialize(_Outptr_result_nullonfailure_ I** ppvObject, TArg1 &&arg1, TArg2 &&arg2, TArg3 &&arg3, TArg4 &&arg4, TArg5 &&arg5, TArg6 &&arg6, TArg7 &&arg7, TArg8 &&arg8, TArg9 &&arg9) throw()  
```

### <a name="parameters"></a>Parametry

*T*  
Klasy określonych przez użytkownika, który dziedziczy z `WRL::RuntimeClass`.

*TArg1*  
Typ argumentu 1, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*TArg2*  
Typ argumentu 2, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*TArg3*  
Typ argumentu 3, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*TArg4*  
Typ argumentu 4, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*TArg5*  
Typ argumentu 5, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*TArg6*  
Typ argumentu 6, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*TArg7*  
Typ argumentu 7, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*TArg8*  
Typ argumentu 8, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*TArg9*  
Typ argumentu 9, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*arg1*  
Argument 1, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*argument2*  
Argument 2, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*arg3*  
Argument 3, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*Arg4*  
Argument 4, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*arg5*  
Argument 5, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*arg6*  
Argument 6, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*arg7*  
Argument 7, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*arg8*  
Argument 8, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*arg9*  
Argument 9, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

## <a name="return-value"></a>Wartość zwracana

Wartość HRESULT.

## <a name="remarks"></a>Uwagi

Zobacz [jak: bezpośrednio utworzyć wystąpienia składników biblioteki WRL](../windows/how-to-instantiate-wrl-components-directly.md) się różnice w tej funkcji i [Microsoft::wrl:: Make](../windows/make-function.md)i aby uzyskać przykład.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)