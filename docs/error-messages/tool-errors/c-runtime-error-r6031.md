---
title: R6031 błąd środowiska uruchomieniowego języka C
ms.date: 11/04/2016
f1_keywords:
- R6031
helpviewer_keywords:
- R6031
ms.assetid: 805d4cd1-cb2f-43fe-87e6-e7bd5b7329c5
ms.openlocfilehash: 6ef3f5fa7d063fdc300e6ac28ca519992525851c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564232"
---
# <a name="c-runtime-error-r6031"></a>R6031 błąd środowiska uruchomieniowego języka C

Próba zainicjowania CRT więcej niż jeden raz. Oznacza to usterkę w aplikacji.

> [!NOTE]
> Jeśli napotkasz ten komunikat o błędzie podczas działania aplikacji, aplikacji został zamknięty, ponieważ ma on wewnętrzny problem. Może to być spowodowane błędów w aplikacji lub przez usterkę w dodatku lub rozszerzenie, które korzysta z aplikacji.
>
> Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
> - Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** naprawić lub zainstalować ponownie program.
> - Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** do usunięcia, należy naprawić lub zainstalować ponownie wszystkie programy dodatków lub rozszerzeń używanych przez aplikację.
> - Sprawdź **Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.
> - Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Diagnostyka wskazuje, że podczas blokady modułu ładującego wykonywały instrukcji MSIL. Aby uzyskać więcej informacji, zobacz [inicjowanie zestawów mieszanych](../../dotnet/initialization-of-mixed-assemblies.md).