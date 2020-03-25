---
title: MakeAndInitialize — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAndInitialize
ms.assetid: 71ceeb12-d2a2-4317-b010-3dcde1b39467
ms.openlocfilehash: 28d9e586a766a131e7ab6280859845810c1d9814
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213801"
---
# <a name="makeandinitialize-function"></a>MakeAndInitialize — Funkcja

Inicjuje określoną klasę środowisko wykonawcze systemu Windows. Ta funkcja służy do tworzenia wystąpienia składnika, który jest zdefiniowany w tym samym module.

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

*&*<br/>
Klasa określona przez użytkownika, która dziedziczy po `WRL::RuntimeClass`.

*TArg1*<br/>
Typ argumentu 1, który jest przesyłany do określonej klasy środowiska uruchomieniowego.

*TArg2*<br/>
Typ argumentu 2, który jest przesyłany do określonej klasy środowiska uruchomieniowego.

*TArg3*<br/>
Typ argumentu 3, który jest przesyłany do określonej klasy środowiska uruchomieniowego.

*TArg4*<br/>
Typ argumentu 4, który jest przesyłany do określonej klasy środowiska uruchomieniowego.

*TArg5*<br/>
Typ argumentu 5, który jest przesyłany do określonej klasy środowiska uruchomieniowego.

*TArg6*<br/>
Typ argumentu 6, który jest przesyłany do określonej klasy środowiska uruchomieniowego.

*TArg7*<br/>
Typ argumentu 7, który jest przesyłany do określonej klasy środowiska uruchomieniowego.

*TArg8*<br/>
Typ argumentu 8, który jest przesyłany do określonej klasy środowiska uruchomieniowego.

*TArg9*<br/>
Typ argumentu 9, który jest przesyłany do określonej klasy środowiska uruchomieniowego.

*arg1*<br/>
Argument 1, który jest przesyłany do określonej klasy środowiska uruchomieniowego.

*arg2*<br/>
Argument 2, który jest przesyłany do określonej klasy środowiska uruchomieniowego.

*arg3*<br/>
Argument 3, który jest przesyłany do określonej klasy środowiska uruchomieniowego.

*arg4*<br/>
Argument 4, który jest przesyłany do określonej klasy środowiska uruchomieniowego.

*arg5*<br/>
Argument 5, który jest przesyłany do określonej klasy środowiska uruchomieniowego.

*arg6*<br/>
Argument 6, który jest przesyłany do określonej klasy środowiska uruchomieniowego.

*arg7*<br/>
Argument 7, który jest przesyłany do określonej klasy środowiska uruchomieniowego.

*arg8*<br/>
Argument 8, który jest przesyłany do określonej klasy środowiska uruchomieniowego.

*arg9*<br/>
Argument 9, który jest przesyłany do określonej klasy środowiska uruchomieniowego.

## <a name="return-value"></a>Wartość zwracana

Wartość HRESULT.

## <a name="remarks"></a>Uwagi

Zobacz [jak: Tworzenie wystąpień WRL składników bezpośrednio](how-to-instantiate-wrl-components-directly.md) , aby poznać różnice między tą funkcją a [firmą Microsoft:: WRL:: Make](make-function.md)i na przykład.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implementuje. h

**Przestrzeń nazw:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](microsoft-wrl-details-namespace.md)
