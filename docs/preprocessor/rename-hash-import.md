---
title: "Zmień nazwę (#import) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- Rename
dev_langs:
- C++
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6391f3d88a081da6e01b115389b1a9b986ae6c0f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="rename-import"></a>zmień nazwę (#import)
**Określonego języka C++**  
  
 Sprawdza się wokół problemów kolizji nazw.  
  
## <a name="syntax"></a>Składnia  
  
```  
rename("OldName","NewName")  
```  
  
#### <a name="parameters"></a>Parametry  
 `OldName`  
 Stara nazwa w bibliotece typów.  
  
 `NewName`  
 Nazwa do użycia zamiast starej nazwy.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ten atrybut jest określony, kompilator zamienia wszystkie wystąpienia *StaraNazwa* w bibliotece typów z podanego użytkownika *NewName* w wynikowej pliki nagłówków.  
  
 Ten atrybut można po nazwie w bibliotece typów pokrywa się z elementem definicji makra w pliki nagłówka systemu. Jeśli ta sytuacja nie uda się rozwiązać, a następnie różne błędy składni zostanie wygenerowany, takich jak [C2059 błąd kompilatora](../error-messages/compiler-errors-1/compiler-error-c2059.md) i [C2061 błąd kompilatora](../error-messages/compiler-errors-1/compiler-error-c2061.md).  
  
> [!NOTE]
>  Zastąpienie dotyczy nazwę w bibliotece typów nie nazwa używana w wynikowym pliku nagłówka.  
  
 Na przykład, załóżmy, że właściwość o nazwie `MyParent` istnieje w bibliotece typów i makra `GetMyParent` jest zdefiniowana w pliku nagłówka i używany przed `#import`. Ponieważ `GetMyParent` jest domyślna nazwa funkcji otoki do obsługi błędów **uzyskać** kolizję nazw właściwości, zostanie przeprowadzona. Aby obejść ten problem, użyj następującego atrybutu w `#import` instrukcji:  
  
```  
rename("MyParent","MyParentX")  
```  
  
 które zmienia nazwę `MyParent` w bibliotece typów. Próba zmiany nazwy `GetMyParent` nazwa otoki zakończy się niepowodzeniem:  
  
```  
rename("GetMyParent","GetMyParentX")  
```  
  
 Jest to spowodowane nazwę `GetMyParent` występuje tylko w wynikowy plik nagłówka biblioteki typów.  
  
 **KOŃCOWY określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)