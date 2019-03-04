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
ms.openlocfilehash: 6afbd7b3a3f4280ad658c1cb9d8802cc3251d0ed
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57291337"
---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d — Przestrzeń nazw

`direct3d` Przestrzeń nazw zawiera funkcje, które obsługują współdziałanie D3D. Go umożliwia bezproblemowe korzystanie z zasobów D3D dla obliczeń w kodzie AMP jak również umożliwia wykorzystanie zasobów utworzonych w AMP, w kodzie D3D, bez tworzenia nadmiarowych kopii pośrednich. Można stopniowo przyspieszyć sekcje intensywnych obliczeń aplikacji DirectX przy użyciu języka C++ AMP i użyć interfejsu API D3D na danych wyprodukowanych z obliczeń AMP.

## <a name="syntax"></a>Składnia

```
namespace direct3d;
```

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[scoped_d3d_access_lock, klasa](scoped-d3d-access-lock-class.md)|Otoka RAII na blokadę dostępu D3D na `accelerator_view` obiektu.|

### <a name="structures"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|[adopt_d3d_access_lock_t, struktura](adopt-d3d-access-lock-t-structure.md)|Typ znacznika wskazujący blokadę dostępu D3D powinien być przyjęte a nie nabyty.|

### <a name="functions"></a>Funkcje

|Nazwa|Opis|
|----------|-----------------|
|[abs](concurrency-direct3d-namespace-functions-amp.md#abs)|Zwraca wartość bezwzględną argumentu|
|[clamp](concurrency-direct3d-namespace-functions-amp.md#clamp)|Przeciążone. Ogranicza _X do określonego zakresu _Min i _Max|
|[countbits —](concurrency-direct3d-namespace-functions-amp.md#countbits)|Zlicza liczbę bitów zestawu w _X|
|[create_accelerator_view](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|Tworzy [accelerator_view, klasa](accelerator-view-class.md) ze wskaźnika do interfejsu urządzenia Direct3D|
|[d3d_access_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|Uzyskaj blokadę na accelerator_view w celu bezpiecznego wykonywania operacji D3D na zasobach współużytkowanych wraz z accelerator_view|
|[d3d_access_try_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|Próba uzyskania blokady dostępu D3D na accelerator_view bez blokowania.|
|[d3d_access_unlock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|Zwolnij blokadę dostępu D3D danego widoku akceleratora.|
|[firstbithigh —](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|Pobiera lokalizację pierwszego ustawionego bitu _X, zaczynając od znaczącego bitu i pracuje w dół|
|[firstbitlow](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|Pobiera lokalizację pierwszego ustawionego bitu _X, zaczynając od znaczącego bitu i pracuje w górę|
|[get_buffer](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|Pobierz interfejs buforu D3D odpowiadający tablicy.|
|[imax](concurrency-direct3d-namespace-functions-amp.md#imax)|Porównuje dwie wartości, zwracając wartość, która jest większa.|
|[imin](concurrency-direct3d-namespace-functions-amp.md#imin)|Porównuje dwie wartości, zwracając wartość, która jest mniejsza.|
|[is_timeout_disabled](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|Zwraca flagę logiczną wskazującą, czy limit czasu jest wyłączony dla określonego obiektu accelerator_view.|
|[mad —](concurrency-direct3d-namespace-functions-amp.md#mad)|Przeciążone. Wykonuje operację arytmetyczną mnożenia/dodawania na trzech argumentach: _X \* _Y + _Z|
|[make_array](concurrency-direct3d-namespace-functions-amp.md#make_array)|Utwórz tablicę ze wskaźnika interfejsu buforu D3D.|
|[noise](concurrency-direct3d-namespace-functions-amp.md#noise)|Generuje losową wartość przy użyciu algorytmu szumu Perlin|
|[wartość w radianach](concurrency-direct3d-namespace-functions-amp.md#radians)|Konwertuje _X ze stopni na radiany|
|[rcp](concurrency-direct3d-namespace-functions-amp.md#rcp)|Oblicza szybko przybliżoną odwrotność argumentu|
|[reversebits —](concurrency-direct3d-namespace-functions-amp.md#reversebits)|Odwraca kolejność bitów w _X|
|[Saturate](concurrency-direct3d-namespace-functions-amp.md#saturate)|Ogranicza _X do zakresu od 0 do 1|
|[sign](concurrency-direct3d-namespace-functions-amp.md#sign)|Przeciążone. Zwraca znak argumentu|
|[smoothstep](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|Zwraca smooth gładką interpolację wielomianu hermite'a pomiędzy 0 a 1, jeśli _X jest w zakresie [_Min, _Max].|
|[step](concurrency-direct3d-namespace-functions-amp.md#step)|Porównuje dwie wartości, zwracając 0 lub 1, w oparciu o wartość, która jest większa|
|[umax](concurrency-direct3d-namespace-functions-amp.md#umax)|Porównuje dwie wartości nieoznaczone, zwracając wartość, która jest większa.|
|[umin](concurrency-direct3d-namespace-functions-amp.md#umin)|Porównuje dwie wartości nieoznaczone, zwracając wartość, która jest mniejsza.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp.h

**Namespace:** Współbieżność

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
