---
title: Make — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Make
helpviewer_keywords:
- Make function
ms.assetid: 66704143-df99-4a95-904d-ed99607e1034
ms.openlocfilehash: ffd0967b741475b260eef80ec24d56874a6bcb1f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213814"
---
# <a name="make-function"></a>Make — Funkcja

Inicjuje określoną klasę środowisko wykonawcze systemu Windows. Ta funkcja służy do tworzenia wystąpienia składnika, który jest zdefiniowany w tym samym module.

## <a name="syntax"></a>Składnia

```cpp
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8,
   typename TArg9
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7,
   TArg8 &&arg8,
   TArg9 &&arg9
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7,
   TArg8 &&arg8
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3
);
template <
   typename T,
   typename TArg1,
   typename TArg2
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2
);
template <
   typename T,
   typename TArg1
>
ComPtr<T> Make(
   TArg1 &&arg1
);
template <
   typename T
>
ComPtr<T> Make();
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

Obiekt `ComPtr<T>`, jeśli się powiedzie; w przeciwnym razie `nullptr`.

## <a name="remarks"></a>Uwagi

Zobacz [jak: Tworzenie wystąpień WRL składników bezpośrednio](how-to-instantiate-wrl-components-directly.md) , aby poznać różnice między tą funkcją i [firmą Microsoft:: WRL::D etails:: MakeAndInitialize](makeandinitialize-function.md), a na przykład.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implementuje. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)
