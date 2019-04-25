---
title: Błąd czasu wykonania języka C R6026
ms.date: 11/04/2016
f1_keywords:
- R6026
helpviewer_keywords:
- R6026
ms.assetid: 7ea751f8-fc20-46ab-99ef-84c95ca0b6b4
ms.openlocfilehash: 28e541b61b6381cd283578a0ce1909e5b39a4a53
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151919"
---
# <a name="c-runtime-error-r6026"></a>Błąd czasu wykonania języka C R6026

Brak wystarczającej ilości miejsca do zainicjowania stdio —

> [!NOTE]
> Jeśli napotkasz ten komunikat o błędzie podczas działania aplikacji, aplikacji został zamknięty, ponieważ ma on wewnętrzny problem z pamięcią. Istnieje kilka możliwych przyczyn tego błędu, ale zazwyczaj jest to spowodowane przez warunek bardzo małej ilości pamięci. Może być także spowodowane przez usterkę w aplikacji, uszkodzenie bibliotek Visual C++, których używa lub sterownika.
>
> Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
> - Zamknij inne aplikacje uruchomione lub uruchom ponownie komputer, aby zwolnić pamięć.
> - Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** naprawić lub zainstalować ponownie program.
> - Jeśli aplikacja była praca przed Ostatnia instalacja innej aplikacji lub sterownika, użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** do usunięcia Nowa aplikacja lub sterownika i spróbuj ponownie aplikację.
> - Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** naprawić lub zainstalować ponownie wszystkie kopie Microsoft Visual C++ Redistributable.
> - Sprawdź **Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.
> - Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Ten błąd występuje, gdy nie ma wystarczającej ilości pamięci do zainicjowania pomocy technicznej standard operacji We/Wy w środowisku uruchomieniowym języka C. Ten błąd zazwyczaj występuje podczas uruchamiania aplikacji. Upewnij się, że Twoja aplikacja i sterowniki i bibliotek DLL, która ładuje nie spowodują uszkodzenia sterty przy uruchamianiu.