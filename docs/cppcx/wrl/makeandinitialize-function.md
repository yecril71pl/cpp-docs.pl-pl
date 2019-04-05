---
title: MakeAndInitialize — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAndInitialize
ms.assetid: 71ceeb12-d2a2-4317-b010-3dcde1b39467
ms.openlocfilehash: 14ae5117194748748ceecf97ac83fc8813bba2d3
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037487"
---
# <a name="makeandinitialize-function"></a>MakeAndInitialize — Funkcja

Inicjuje określonej klasy środowiska wykonawczego Windows. Ta funkcja służy do utworzenia wystąpienia składnika, który jest zdefiniowany w tym samym module.

## <a name="syntax"></a>Składnia

```cpp
template <
    typename T,
    typename I,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8,
    typename TArg9>
HRESULT MakeAndInitialize(
    _Outptr_result_nullonfailure_ I** ppvObject,
    TArg1 &&arg1,
    TArg2 &&arg2,
    TArg3 &&arg3,
    TArg4 &&arg4,
    TArg5 &&arg5,
    TArg6 &&arg6,
    TArg7 &&arg7,
    TArg8 &&arg8,
    TArg9 &&arg9) throw()
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

Zobacz [jak: Składników biblioteki WRL bezpośrednie tworzenie wystąpień](how-to-instantiate-wrl-components-directly.md) się różnice w tej funkcji i [Microsoft::wrl:: Make](make-function.md)i aby uzyskać przykład.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL::Details — Przestrzeń nazw](microsoft-wrl-details-namespace.md)