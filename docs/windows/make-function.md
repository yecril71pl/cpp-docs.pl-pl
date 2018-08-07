---
title: Ustaw funkcję | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Make
dev_langs:
- C++
helpviewer_keywords:
- Make function
ms.assetid: 66704143-df99-4a95-904d-ed99607e1034
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9941f2b1bce67fb09c69db6278de94c102f88473
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604872"
---
# <a name="make-function"></a>Make — Funkcja
Inicjuje określonej klasy środowiska wykonawczego Windows. Ta funkcja służy do utworzenia wystąpienia składnika, który jest zdefiniowany w tym samym module.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 A `ComPtr<T>` obiektu w przypadku powodzenia; w przeciwnym razie **nullptr**.  
  
## <a name="remarks"></a>Uwagi  
 Zobacz [jak: bezpośrednio utworzyć wystąpienia składników biblioteki WRL](../windows/how-to-instantiate-wrl-components-directly.md) się różnice w tej funkcji i [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)i aby uzyskać przykład.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)