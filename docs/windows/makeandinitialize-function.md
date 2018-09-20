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
ms.openlocfilehash: 05f577ce8845b85cdb3a263aaea1e8c2cdb0f240
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409184"
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

*T*<br/>
Klasy określonych przez użytkownika, który dziedziczy z `WRL::RuntimeClass`.

*TArg1*<br/>
Typ argumentu 1, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*TArg2*<br/>
Typ argumentu 2, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*TArg3*<br/>
Typ argumentu 3, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*TArg4*<br/>
Typ argumentu 4, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*TArg5*<br/>
Typ argumentu 5, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*TArg6*<br/>
Typ argumentu 6, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*TArg7*<br/>
Typ argumentu 7, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*TArg8*<br/>
Typ argumentu 8, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*TArg9*<br/>
Typ argumentu 9, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*arg1*<br/>
Argument 1, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*argument2*<br/>
Argument 2, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*arg3*<br/>
Argument 3, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*Arg4*<br/>
Argument 4, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*arg5*<br/>
Argument 5, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*arg6*<br/>
Argument 6, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*arg7*<br/>
Argument 7, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*arg8*<br/>
Argument 8, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*arg9*<br/>
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