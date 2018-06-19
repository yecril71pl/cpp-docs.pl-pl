---
title: Przekazywanie dalej typu (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- type forwarding, Visual C++
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9caa2e18a1ec851967857eb068797e092835f587
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891097"
---
# <a name="type-forwarding-ccli"></a>Przekazywanie dalej typu (C++/CLI)
*Przekazywanie dalej typu* umożliwia przeniesienie typu z jednego zestawu (zestawów A) do innego zestawu (zestawów B) tak, aby nie jest konieczne ponowne skompilowanie klienci używający zestawu A.  
  
## <a name="all-platforms"></a>Wszystkie platformy  
 Ta funkcja nie jest obsługiwana w wszystkich środowisk uruchomieniowych.  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 Ta funkcja nie jest obsługiwana w środowisku wykonawczym systemu Windows.  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania  
 Poniższy przykład kodu pokazuje, jak używać przekazywanie dalej typu.  
  
### <a name="syntax"></a>Składnia  
  
```  
#using "new.dll"  
[assembly:TypeForwardedTo(type::typeid)];  
```  
  
### <a name="parameters"></a>Parametry  
 `new`  
 Zestaw, do którego chcesz przenieść definicji typu.  
  
 `type`  
 Typ definicji, którego chcesz przenieść do innego zestawu.  
  
### <a name="remarks"></a>Uwagi  
 Po składnikiem (assembly) jest dostarczany i jest używany przez aplikacje klienckie służy typu przekazywania ich do przenoszenia typu ze składników (assembly) do innego zestawu, Wydaj zaktualizowanych składników (i wszelkie dodatkowe zestawy wymagane) i klienta aplikacje będą nadal działać bez jest ponownie kompilowana.  
  
 Przekazywanie dalej typu działa tylko dla składników odwołuje się istniejących aplikacji. Po odbudowaniu aplikacji musi być referencje zestawu odpowiednie dla wszystkich typów używane w aplikacji.  
  
 Podczas przesyłania dalej typu (typ A) z zestawu, należy dodać `TypeForwardedTo` atrybutu dla tego typu, a także odwołania do zestawu. Zestaw, do której odwołuje się musi zawierać jedną z następujących czynności:  
  
-   Definicja typu A.  
  
-   A `TypeForwardedTo` atrybutu dla typu A, jak również odwołania do zestawu.  
  
 Przykłady typów, które mogą być przekazywane obejmują:  
  
-   klasy REF  
  
-   klasy wartości  
  
-   typy wyliczeniowe  
  
-   interfejsy  
  
 Nie można przesłać dalej następujących typów:  
  
-   Typy ogólne  
  
-   Typy natywne  
  
-   Zagnieżdżone typy (Jeśli chcesz przesłać dalej typu zagnieżdżonego, należy przesyłania dalej typ otaczający)  
  
 Można przekazać dalej typ do zestawu utworzone w dowolnym języku przeznaczonych dla środowiska CLR.  
  
 Zatem w przypadku pliku kodu źródłowego, który jest używany do tworzenia zestawu A.dll zawiera definicję typu (`ref class MyClass`), i chcesz przenieść typu definicji zestawu B.dll, jak:  
  
1.  Przenieś `MyClass` definicji do pliku kodu źródłowego, używany do tworzenia B.dll typu.  
  
2.  Tworzenie zestawu B.dll  
  
3.  Usuń `MyClass` wpisz definicji z kodu źródłowego, używane do tworzenia A.dll i zastąp go następującym kodem:  
  
    ```  
    #using "B.dll"  
    [assembly:TypeForwardedTo(MyClass::typeid)];  
    ```  
  
4.  Tworzenie zestawu A.dll.  
  
5.  Użyj A.dll bez konieczności ponownego kompilowania aplikacji klienckich.  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**