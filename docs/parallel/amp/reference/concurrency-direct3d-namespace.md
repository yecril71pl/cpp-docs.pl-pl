---
title: Concurrency::direct3d — Przestrzeń nazw
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::direct3d
- amprt/Concurrency::direct3d
- amp_short_vectors/Concurrency::direct3d
- amp_graphics/Concurrency::direct3d
- amp_math/Concurrency::direct3d
helpviewer_keywords:
- direct3d namespace
ms.assetid: 9566a2f1-4d5f-43e4-a3ac-676643d38420
ms.openlocfilehash: e1374acbd7061afaba372100cf6e69d9d717da8a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127036"
---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d — Przestrzeń nazw

Przestrzeń nazw `direct3d` zawiera funkcje, które obsługują współdziałanie D3D. Umożliwia korzystanie z zasobów D3D do obliczeń w kodzie AMP. Umożliwia również korzystanie z zasobów utworzonych w AMP w kodzie D3D bez tworzenia nadmiarowych kopii pośrednich. Możesz stopniowo przyspieszyć sekcje intensywnych obliczeń aplikacji DirectX, używając C++ amp, i korzystając z interfejsu API D3D na danych wyprodukowanych z obliczeń amp.

## <a name="syntax"></a>Składnia

```cpp
namespace direct3d;
```

## <a name="members"></a>Members

### <a name="classes"></a>Klasy

|Name (Nazwa)|Opis|
|----------|-----------------|
|[scoped_d3d_access_lock, klasa](scoped-d3d-access-lock-class.md)|Otoka RAII dla blokady dostępu D3D na obiekcie `accelerator_view`.|

### <a name="structures"></a>Struktury

|Name (Nazwa)|Opis|
|----------|-----------------|
|[adopt_d3d_access_lock_t, struktura](adopt-d3d-access-lock-t-structure.md)|Typ tagu wskazujący, że blokada dostępu D3D powinna zostać przyjęta, a nie pobrana.|

### <a name="functions"></a>Funkcje

|Name (Nazwa)|Opis|
|----------|-----------------|
|[ABS](concurrency-direct3d-namespace-functions-amp.md#abs)|Zwraca wartość bezwzględną argumentu.|
|[opraw](concurrency-direct3d-namespace-functions-amp.md#clamp)|Przeciążone. Ogranicza _X do określonego _Min i zakresu _Max|
|[countbits —](concurrency-direct3d-namespace-functions-amp.md#countbits)|Zlicza liczbę bitów zestawu w _X|
|[create_accelerator_view](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|Tworzy [klasę accelerator_view](accelerator-view-class.md) ze wskaźnika do interfejsu urządzenia Direct3D|
|[d3d_access_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|Uzyskuje blokadę accelerator_view do bezpiecznego wykonywania operacji D3D na zasobach współużytkowanych z accelerator_view|
|[d3d_access_try_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|Spróbuj uzyskać blokadę dostępu D3D na accelerator_view bez blokowania.|
|[d3d_access_unlock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|Zwolnij blokadę dostępu D3D dla danego accelerator_view.|
|[firstbithigh —](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|Pobiera lokalizację pierwszego zestawu bit w _X, rozpoczynając od najwyższego porządku i działającego w dół|
|[firstbitlow —](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|Pobiera lokalizację pierwszego zestawu bit w _X, rozpoczynając od najniższego bitu kolejności i działającego w górę|
|[get_buffer](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|Pobierz interfejs buforu D3D jako tablicę źródłową.|
|[imax](concurrency-direct3d-namespace-functions-amp.md#imax)|Porównuje dwie wartości, zwracając wartość, która jest większa.|
|[imin](concurrency-direct3d-namespace-functions-amp.md#imin)|Porównuje dwie wartości, zwracając wartość, która jest mniejsza.|
|[is_timeout_disabled](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|Zwraca flagę logiczną wskazującą, czy limit czasu jest wyłączony dla określonego accelerator_view.|
|[Mad —](concurrency-direct3d-namespace-functions-amp.md#mad)|Przeciążone. Wykonuje arytmetyczną operację mnożenia/dodawania na trzech argumentach: _X \* _Y + _Z|
|[make_array](concurrency-direct3d-namespace-functions-amp.md#make_array)|Utwórz tablicę ze wskaźnika interfejsu buforu D3D.|
|[emitowan](concurrency-direct3d-namespace-functions-amp.md#noise)|Generuje losową wartość przy użyciu algorytmu szumu w języku Perl|
|[radianach](concurrency-direct3d-namespace-functions-amp.md#radians)|Konwertuje _X z stopni na radiany|
|[Analiza](concurrency-direct3d-namespace-functions-amp.md#rcp)|Oblicza szybką i przybliżoną odwrotność argumentu|
|[reversebits —](concurrency-direct3d-namespace-functions-amp.md#reversebits)|Odwraca kolejność bitów w _X|
|[Saturate —](concurrency-direct3d-namespace-functions-amp.md#saturate)|Powoduje, że _X w zakresie od 0 do 1|
|[sign](concurrency-direct3d-namespace-functions-amp.md#sign)|Przeciążone. Zwraca znak argumentu.|
|[smoothstep —](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|Zwraca gładką interpolację Hermite z zakresu od 0 do 1, jeśli _X należy do zakresu [_Min, _Max].|
|[czynności](concurrency-direct3d-namespace-functions-amp.md#step)|Porównuje dwie wartości, zwracając wartość 0 lub 1 na podstawie wartości większej|
|[UMAX](concurrency-direct3d-namespace-functions-amp.md#umax)|Porównuje dwie wartości bez znaku, zwracając wartość, która jest większa.|
|[umin](concurrency-direct3d-namespace-functions-amp.md#umin)|Porównuje dwie wartości bez znaku, zwracając wartość, która jest mniejsza.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp. h

**Przestrzeń nazw:** Współbieżności

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
