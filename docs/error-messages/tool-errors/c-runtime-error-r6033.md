---
title: Błąd czasu wykonania języka C R6033
ms.date: 11/04/2016
f1_keywords:
- R6033
helpviewer_keywords:
- R6033
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
ms.openlocfilehash: 39d8a20dacb0cdeb2a767529e9716bd476f406dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400009"
---
# <a name="c-runtime-error-r6033"></a>Błąd czasu wykonania języka C R6033

Próba użycia MSIL kod z tego zestawu podczas inicjowania kodu natywnego. Oznacza to usterkę w aplikacji. Jest to najprawdopodobniej wynikiem wywołania skompilowany MSIL (/ clr) — funkcja natywnego konstruktora lub z funkcji DllMain.

> [!NOTE]
> Jeśli napotkasz ten komunikat o błędzie podczas działania aplikacji, aplikacji został zamknięty, ponieważ ma on wewnętrzny problem. Ten błąd może być spowodowany przez usterkę w aplikacji lub usterkę w dodatku lub rozszerzenia, która jest używana.
>
> Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
> - Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** naprawić lub zainstalować ponownie program.
> - Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** do usunięcia, napraw lub ponownie zainstalować wszystkie rozszerzeń lub dodatków.
> - Sprawdź **Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.
> - Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Diagnostyka wskazuje, że podczas blokady modułu ładującego wykonywały instrukcji MSIL. Może to występować, jeśli skompilowałeś natywnych języka C++ za pomocą flagi/CLR. Flagi/CLR można używać tylko w przypadku modułów, które zawierają kodu zarządzanego. Aby uzyskać więcej informacji, zobacz [inicjowanie zestawów mieszanych](../../dotnet/initialization-of-mixed-assemblies.md).