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
ms.openlocfilehash: 44b76e1a3eaff778fc64806eec49eff1bf2a10eb
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596672"
---
# <a name="type-forwarding-ccli"></a>Przekazywanie dalej typu (C++/CLI)

*Przekazywanie dalej typu* pozwala na przenoszenie typu z jednego zestawu (assembly A) do innego zestawu (assembly B), taki sposób, że nie jest konieczne ponownie skompilować klientów korzystających z zestawu A.

## <a name="all-platforms"></a>Wszystkie platformy

Ta funkcja nie jest obsługiwana w wszystkie środowiska wykonawcze.

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Ta funkcja nie jest obsługiwana w środowisku uruchomieniowym Windows.

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

Poniższy przykład kodu demonstruje sposób używania przekazywanie dalej typu.

### <a name="syntax"></a>Składnia

```
#using "new.dll"
[assembly:TypeForwardedTo(type::typeid)];
```

### <a name="parameters"></a>Parametry

*new*  
Zestaw, do którego chcesz przenieść definicji typu.

*Typ*  
Typ, których definicje są przenoszone do innego zestawu.

### <a name="remarks"></a>Uwagi

Po części (assembly) jest dostarczany jest używana przez aplikacje klienckie, służy typu przekazywania przenieść typu składnika (assembly) do innego zestawu, dostarczaj aktualizowanego składnika (i wszelkie dodatkowe zestawy wymagane) i klienta aplikacje będą nadal działać bez są ponownie kompilowane.

Przekazywanie dalej typu działa tylko dla składników przywoływane przez istniejące aplikacje. Podczas ponownego kompilowania aplikacji to musi istnieć odpowiednie odwołania do zestawów dla wszystkich typów używanych w aplikacji.

Podczas przesyłania dalej typu (typ A) z zestawu, należy dodać `TypeForwardedTo` atrybutu dla tego typu, a także odwołania do zestawu. Zestaw, do którego można odwołać się musi zawierać jeden z następujących czynności:

- Definicja typu A.

- A `TypeForwardedTo` atrybutu dla typu A, jak również odwołania do zestawu.

Przykłady typów, które mogą być przekazywane między innymi:

- klasy REF

- klasy wartości

- typy wyliczeniowe

- interfejsy

Nie można przesłać dalej następujących typów:

- Typy ogólne

- Typy natywne

- Zagnieżdżone typy (Jeśli chcesz przesłać dalej typu zagnieżdżonego, powinien przesyłania dalej typ otaczający)

Można przekazać dalej typ do zestawu, który został utworzony w dowolnym języku, przeznaczone dla środowiska uruchomieniowego języka wspólnego.

Tak, jeśli plik kodu źródłowego, który jest używany do tworzenia zestawu A.dll zawiera definicję dla typu (`ref class MyClass`), i chcesz przenieść ten typ definicji do zestawu B.dll, jak:

1. Przenieś `MyClass` definicji do pliku kodu źródłowego, używany do tworzenia B.dll typu.

2. Kompilacja zestawów B.dll

3. Usuń `MyClass` wpisz definicję z kodu źródłowego, używane do tworzenia A.dll i zastąp go następującym kodem:

    ```
    #using "B.dll"
    [assembly:TypeForwardedTo(MyClass::typeid)];
    ```

4. Kompilacja zestawów A.dll.

5. Użyj A.dll bez konieczności ponownego kompilowania aplikacji klienckich.

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`