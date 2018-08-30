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
ms.openlocfilehash: 68283d8dc0e8b2152b28a2fe2990ddc22fafa6d3
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196400"
---
# <a name="ustringorid-class"></a>Klasa _U_STRINGorID
Ta klasa adaptera argument umożliwia nazw zasobów (LPCTSTRs) lub identyfikatory zasobów (UINTs), który zostanie przekazany do funkcji bez konieczności obiekt wywołujący, aby przekonwertować na ciąg przy użyciu makra MAKEINTRESOURCE identyfikator.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
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
 Ta klasa jest przeznaczona dla takich jak wdrażanie otoki, aby interfejs API zarządzania zasobami Windows [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea), [LoadIcon](/windows/desktop/api/winuser/nf-winuser-loadicona), i [LoadMenu](/windows/desktop/api/winuser/nf-winuser-loadmenua) funkcji, które akceptują argument LPCTSTR, który może być nazwy zasobu lub jego identyfikator.  
  
 Klasa definiuje dwa przeciążenia konstruktora: przyjmuje jeden LPCTSTR argument, a druga akceptuje UINT argument. UINT argument jest konwertowany na typ zasobu, zgodny z funkcji zarządzania zasobami Windows przy użyciu makra MAKEINTRESOURCE i wynik przechowywany w element członkowski danych jednej klasy, [m_lpstr](#_u_stringorid__m_lpstr). Argument Pro Konstruktor LPCTSTR są przechowywane bezpośrednio, bez konwersji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  
  
##  <a name="_u_stringorid__m_lpstr"></a>  _U_STRINGorID::m_lpstr  
 Klasa przechowuje wartość przekazana do jednej z jego konstruktorów jako publicznej składowej danych LPCTSTR.  
  
```
LPCTSTR m_lpstr;
```  
  
##  <a name="_u_stringorid___u_stringorid"></a>  _U_STRINGorID::_U_STRINGorID  
 Konstruktor UINT konwertuje jej argument niezgodny z funkcji zarządzania zasobami Windows przy użyciu makra MAKEINTRESOURCE typu zasobu, a wynik jest przechowywany w elemencie członkowskim danych jednego tej klasy, [m_lpstr](#_u_stringorid__m_lpstr).  
  
```
_U_STRINGorID(UINT nID);  
_U_STRINGorID(LPCTSTR lpString);
```  
  
### <a name="parameters"></a>Parametry  
 *nID*  
 Identyfikator zasobu.  
  
 *lpString*  
 Nazwa zasobu.  
  
### <a name="remarks"></a>Uwagi  
 Argument Pro Konstruktor LPCTSTR są przechowywane bezpośrednio, bez konwersji.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
