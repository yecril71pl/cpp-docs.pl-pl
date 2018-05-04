---
title: Klasa _U_STRINGorID | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL._U_STRINGorID
- ATL::_U_STRINGorID
- _U_STRINGorID
dev_langs:
- C++
helpviewer_keywords:
- _U_STRINGorID class
- U_STRINGorID class
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2a601b1c64b28681c13a0b9e8f42156d8820cb4b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ustringorid-class"></a>Klasa _U_STRINGorID
Ta klasa karta argument umożliwia albo nazw zasobów ( `LPCTSTR`s) lub identyfikatory zasobów ( **UINT**s) mają być przekazane do funkcji bez konieczności obiekt wywołujący, aby przekonwertować ciąg za pomocą Identyfikatora **MAKEINTRESOURCE** makra.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class _U_STRINGorID
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[_U_STRINGorID::_U_STRINGorID](#_u_stringorid___u_stringorid)|Konstruktor.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[_U_STRINGorID::m_lpstr](#_u_stringorid__m_lpstr)|Identyfikator zasobu.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa jest przeznaczony do implementacji otoki interfejsu API Menedżera zasobów systemu Windows, takich jak [FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042), [LoadIcon](http://msdn.microsoft.com/library/windows/desktop/ms648072), i [LoadMenu](http://msdn.microsoft.com/library/windows/desktop/ms647990) funkcji, które akceptują `LPCTSTR` argumentu, który może być nazwa zasobu lub jego identyfikator.  
  
 Klasa definiuje dwa przeciążenia konstruktora: jeden akceptuje `LPCTSTR` akceptuje argument, a druga **UINT** argumentu. **UINT** argument jest konwertowana na typ zasobu zgodne z funkcji zarządzania zasobami systemu Windows przy użyciu **MAKEINTRESOURCE** makro i wynik przechowywany w element członkowski danych klasy, [m_lpstr](#_u_stringorid__m_lpstr). Argument `LPCTSTR` konstruktora są przechowywane bezpośrednio, bez konwersji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  
  
##  <a name="_u_stringorid__m_lpstr"></a>  _U_STRINGorID::m_lpstr  
 Klasa zawiera wartość przekazywane do jednego z jego konstruktorów jako publiczną `LPCTSTR` element członkowski danych.  
  
```
LPCTSTR m_lpstr;
```  
  
##  <a name="_u_stringorid___u_stringorid"></a>  _U_STRINGorID::_U_STRINGorID  
 **UINT** Konstruktor konwertuje jej argument typu zasobu zgodne z funkcji zarządzania zasobami systemu Windows przy użyciu **MAKEINTRESOURCE** makro i wynik są przechowywane w jednym klasy element członkowski danych, [m_lpstr](#_u_stringorid__m_lpstr).  
  
```
_U_STRINGorID(UINT nID);  
_U_STRINGorID(LPCTSTR lpString);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Identyfikator zasobu.  
  
 `lpString`  
 Nazwa zasobu.  
  
### <a name="remarks"></a>Uwagi  
 Argument `LPCTSTR` konstruktora są przechowywane bezpośrednio, bez konwersji.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
