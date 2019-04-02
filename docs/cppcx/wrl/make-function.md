---
title: Make — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Make
helpviewer_keywords:
- Make function
ms.assetid: 66704143-df99-4a95-904d-ed99607e1034
ms.openlocfilehash: cab261724399107c57b36a9020906a96697f7eca
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786805"
---
# <a name="make-function"></a>Make — Funkcja

Inicjuje określonej klasy środowiska wykonawczego Windows. Ta funkcja służy do utworzenia wystąpienia składnika, który jest zdefiniowany w tym samym module.

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

*arg2*<br/>
Argument 2, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*arg3*<br/>
Argument 3, który jest przekazywany do określonego środowiska uruchomieniowego klasy.

*arg4*<br/>
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

A `ComPtr<T>` obiektu w przypadku powodzenia; w przeciwnym razie `nullptr`.

## <a name="remarks"></a>Uwagi

Zobacz [jak: Składników biblioteki WRL bezpośrednie tworzenie wystąpień](how-to-instantiate-wrl-components-directly.md) się różnice w tej funkcji i [Microsoft::WRL::Details::MakeAndInitialize](makeandinitialize-function.md)i aby uzyskać przykład.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)