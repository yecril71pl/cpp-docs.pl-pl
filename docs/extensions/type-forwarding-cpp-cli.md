---
title: Przekazywanie dalej typu (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- type forwarding, C++
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
ms.openlocfilehash: 0803ecc2ffb2da2748b1ef063481aa2571f27f50
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171934"
---
# <a name="type-forwarding-ccli"></a>Przekazywanie dalej typu (C++/CLI)

*Przekazywanie typu* umożliwia przeniesienie typu z jednego zestawu (zestawu a) do innego zestawu (zestawu B), tak aby nie trzeba było ponownie kompilować klientów korzystających z zestawu a.

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Ta funkcja nie jest obsługiwana w środowisko wykonawcze systemu Windows.

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

Poniższy przykład kodu demonstruje, jak używać przekazywania typu.

### <a name="syntax"></a>Składnia

```cpp
#using "new.dll"
[assembly:TypeForwardedTo(type::typeid)];
```

### <a name="parameters"></a>Parametry

*new*<br/>
Zestaw, do którego jest przenoszona definicja typu.

*type*<br/>
Typ, którego definicja jest przenoszona do innego zestawu.

### <a name="remarks"></a>Uwagi

Gdy składnik (zestaw) jest używany przez aplikacje klienckie, można użyć przesyłania dalej typu w celu przeniesienia typu z składnika (zestawu) do innego zestawu, wysłania zaktualizowanego składnika (oraz wszelkich dodatkowych wymaganych zestawów) i klienta programu aplikacje będą nadal działały bez ponownej kompilacji.

Przekazywanie typu działa tylko dla składników, do których odwołują się istniejące aplikacje. Podczas odbudowywania aplikacji muszą istnieć odpowiednie odwołania do zestawów dla wszystkich typów używanych w aplikacji.

Podczas przekazywania typu (typu A) z zestawu, należy dodać atrybut `TypeForwardedTo` dla tego typu, a także odwołanie do zestawu. Zestaw, do którego się odwołuje, musi zawierać jedną z następujących czynności:

- Definicja typu A.

- Atrybut `TypeForwardedTo` typu A, a także odwołanie do zestawu.

Przykłady typów, które mogą być przekazywane, obejmują:

- klasy referencyjne

- klasy wartości

- typy wyliczeniowe

- interfejsy

Nie można przekazywać następujących typów:

- Typy ogólne

- Typy natywne

- Zagnieżdżone typy (Jeśli chcesz przekazywać Typ zagnieżdżony, należy przekazać typ otaczający)

Można przesłać dalej typ do zestawu, który został utworzony w dowolnym języku przeznaczonym dla środowiska uruchomieniowego języka wspólnego.

Tak więc, jeśli plik kodu źródłowego, który jest używany do kompilowania zestawu A. dll zawiera definicję typu (`ref class MyClass`) i chcesz przenieść definicję tego typu do zestawu B. dll, można:

1. Przenieś definicję typu `MyClass` do pliku kodu źródłowego użytego do skompilowania B. dll.

2. Kompiluj zestaw B. dll

3. Usuń definicję typu `MyClass` z kodu źródłowego użytego do skompilowania biblioteki. dll i Zastąp ją następującym:

    ```cpp
    #using "B.dll"
    [assembly:TypeForwardedTo(MyClass::typeid)];
    ```

4. Kompiluj zestaw A. dll.

5. Użyj. dll bez ponownego kompilowania aplikacji klienckich.

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/clr`
