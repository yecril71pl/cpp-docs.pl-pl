---
title: CONCURRENCY::Direct3D — Namespace | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- amp/Concurrency::direct3d
- amprt/Concurrency::direct3d
- amp_short_vectors/Concurrency::direct3d
- amp_graphics/Concurrency::direct3d
- amp_math/Concurrency::direct3d
dev_langs:
- C++
helpviewer_keywords:
- direct3d namespace
ms.assetid: 9566a2f1-4d5f-43e4-a3ac-676643d38420
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9516e3f89d393405a5f71af569a50e46e381d579
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d — Przestrzeń nazw
`direct3d` Przestrzeń nazw zawiera funkcje, które obsługują współdziałanie D3D. Go umożliwia bezproblemowe na użytek D3D zasobów obliczeniowych w kodzie AMP także Zezwalaj na korzystanie z zasobów utworzone w AMP w kodzie D3D bez tworzenia nadmiarowe kopie pośrednich. Można przyrostowo przyspieszanie znacznym obliczeń części aplikacji DirectX przy użyciu C++ AMP i na podstawie obliczenia AMP danych za pomocą interfejsu API D3D.  
  
## <a name="syntax"></a>Składnia  
  
```  
namespace direct3d;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="classes"></a>Klasy  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[scoped_d3d_access_lock, klasa](scoped-d3d-access-lock-class.md)|Otoka RAII dla dostępu D3D blokadę `accelerator_view` obiektu.|  
  
### <a name="structures"></a>Struktury  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[adopt_d3d_access_lock_t, struktura](adopt-d3d-access-lock-t-structure.md)|Typie tag, aby określić blokowania dostępu D3D powinny być przyjęte zamiast nabyte.|  
  
### <a name="functions"></a>Funkcje  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ABS](concurrency-direct3d-namespace-functions-amp.md#abs)|Zwraca wartość bezwzględną argumentu|  
|[ograniczenie](concurrency-direct3d-namespace-functions-amp.md#clamp)|Przeciążone. Zawęża _X do określonego zakresu _min — i _maksymalny|  
|[countbits —](concurrency-direct3d-namespace-functions-amp.md#countbits)|Oblicza liczbę bitów zestawu _X|  
|[create_accelerator_view](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|Tworzy [accelerator_view — klasa](accelerator-view-class.md) ze wskaźnika do interfejsu urządzenia Direct3D|  
|[d3d_access_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|Uzyskuje blokadę accelerator_view na potrzeby bezpiecznego wykonywanie operacji D3D zasobów udostępnionych z accelerator_view|  
|[d3d_access_try_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|Próba uzyskania dostępu D3D blokadę accelerator_view bez blokowania.|  
|[d3d_access_unlock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|Zwalnia blokadę D3D dostępu na danym accelerator_view.|  
|[firstbithigh —](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|Pobiera lokalizację pierwszy bit zestawu w _X, rozpoczynając od bitu najwyższego rzędu i Praca w dół|  
|[firstbitlow —](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|Pobiera lokalizację pierwszy bit zestawu w _X, zaczynając od najniższy bit kolejności i Praca w górę|  
|[get_buffer](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|Pobierz interfejs buforu D3D bazowy tablicy.|  
|[imax](concurrency-direct3d-namespace-functions-amp.md#imax)|Porównuje dwie wartości, zwraca wartość, która jest większa.|  
|[imin](concurrency-direct3d-namespace-functions-amp.md#imin)|Porównuje dwie wartości, zwraca wartość, która jest mniejsza.|  
|[is_timeout_disabled](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|Zwraca wartość boolean flagę wskazującą, czy limit czasu jest wyłączona dla określonego accelerator_view.|  
|[mad —](concurrency-direct3d-namespace-functions-amp.md#mad)|Przeciążone. Wykonuje arytmetyczne mnożenia/Dodaj operacji na trzech argumentów: _X * _Y + _Z —|  
|[make_array](concurrency-direct3d-namespace-functions-amp.md#make_array)|Utwórz tablicy ze wskaźnikiem interfejsu buforu D3D.|  
|[hałasu](concurrency-direct3d-namespace-functions-amp.md#noise)|Generuje losowe wartości przy użyciu algorytmu szumu Perlin|  
|[wartość w radianach](concurrency-direct3d-namespace-functions-amp.md#radians)|Konwertuje _X stopnie na radiany|  
|[rcp](concurrency-direct3d-namespace-functions-amp.md#rcp)|Oblicza szybkie, przybliżone odwrotność argumentu|  
|[reversebits —](concurrency-direct3d-namespace-functions-amp.md#reversebits)|Odwraca kolejność bitów w _X|  
|[saturate —](concurrency-direct3d-namespace-functions-amp.md#saturate)|Zawęża _X liczbą z zakresu od 0 do 1|  
|[sign](concurrency-direct3d-namespace-functions-amp.md#sign)|Przeciążone. Zwraca znak argumentu|  
|[smoothstep](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|Zwraca smooth interpolacji Hermite od 0 do 1, jeśli _X znajduje się w zakresie [_min —, _maksymalny].|  
|[Krok](concurrency-direct3d-namespace-functions-amp.md#step)|Porównuje dwie wartości, zwraca 0 lub 1, w oparciu o wartość, która jest większa|  
|[umax](concurrency-direct3d-namespace-functions-amp.md#umax)|Porównuje dwie wartości bez znaku, zwracając wartość, która jest większa.|  
|[umin](concurrency-direct3d-namespace-functions-amp.md#umin)|Porównuje dwie wartości bez znaku, zwracając wartość, która jest mniejsza.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amp.h  
  
 **Namespace:** współbieżności  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
