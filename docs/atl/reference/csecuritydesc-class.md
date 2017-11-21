---
title: Klasa CSecurityDesc | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc::CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc::FromString
- ATLSECURITY/ATL::CSecurityDesc::GetControl
- ATLSECURITY/ATL::CSecurityDesc::GetDacl
- ATLSECURITY/ATL::CSecurityDesc::GetGroup
- ATLSECURITY/ATL::CSecurityDesc::GetOwner
- ATLSECURITY/ATL::CSecurityDesc::GetPSECURITY_DESCRIPTOR
- ATLSECURITY/ATL::CSecurityDesc::GetSacl
- ATLSECURITY/ATL::CSecurityDesc::IsDaclAutoInherited
- ATLSECURITY/ATL::CSecurityDesc::IsDaclDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsDaclPresent
- ATLSECURITY/ATL::CSecurityDesc::IsDaclProtected
- ATLSECURITY/ATL::CSecurityDesc::IsGroupDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsOwnerDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsSaclAutoInherited
- ATLSECURITY/ATL::CSecurityDesc::IsSaclDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsSaclPresent
- ATLSECURITY/ATL::CSecurityDesc::IsSaclProtected
- ATLSECURITY/ATL::CSecurityDesc::IsSelfRelative
- ATLSECURITY/ATL::CSecurityDesc::MakeAbsolute
- ATLSECURITY/ATL::CSecurityDesc::MakeSelfRelative
- ATLSECURITY/ATL::CSecurityDesc::SetControl
- ATLSECURITY/ATL::CSecurityDesc::SetDacl
- ATLSECURITY/ATL::CSecurityDesc::SetGroup
- ATLSECURITY/ATL::CSecurityDesc::SetOwner
- ATLSECURITY/ATL::CSecurityDesc::SetSacl
- ATLSECURITY/ATL::CSecurityDesc::ToString
dev_langs: C++
helpviewer_keywords: CSecurityDesc class
ms.assetid: 3767a327-378f-4690-ba40-4d9f6a1f5ee4
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1a46a501c443baa65ab4c6da8bc4524c53e44989
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="csecuritydesc-class"></a>Klasa CSecurityDesc
Ta klasa jest otoki dla **SECURITY_DESCRIPTOR** struktury.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CSecurityDesc
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSecurityDesc::CSecurityDesc](#csecuritydesc)|Konstruktor.|  
|[CSecurityDesc:: ~ CSecurityDesc](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSecurityDesc::FromString](#fromstring)|Konwertuje deskryptora zabezpieczeń format ciągu deskryptora zabezpieczeń prawidłowy, funkcjonalności.|  
|[CSecurityDesc::GetControl](#getcontrol)|Pobiera kontrolować informacji z deskryptora zabezpieczeń.|  
|[CSecurityDesc::GetDacl](#getdacl)|Pobiera DACL kontroli dostępu (DACL) listy informacji z deskryptora zabezpieczeń.|  
|[CSecurityDesc::GetGroup](#getgroup)|Pobiera informacje o podstawowej grupy z deskryptora zabezpieczeń.|  
|[CSecurityDesc::GetOwner](#getowner)|Pobiera informacje właściciela z deskryptora zabezpieczeń.|  
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|Zwraca wskaźnik do **SECURITY_DESCRIPTOR** struktury.|  
|[CSecurityDesc::GetSacl](#getsacl)|Pobiera informacje o systemie kontroli dostępu (SACL) listy z deskryptora zabezpieczeń.|  
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|Określa, jeśli lista DACL jest skonfigurowany do obsługi automatycznych propagacji.|  
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|Określa, czy domyślnie DACL skonfigurowano deskryptora zabezpieczeń.|  
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|Określa, czy deskryptora zabezpieczeń zawiera listy DACL.|  
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|Określa, czy lista DACL jest skonfigurowany do uniemożliwiają zmiany.|  
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|Określa, czy identyfikator zabezpieczeń grupy deskryptora zabezpieczeń (SID) została ustawiona domyślnie.|  
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|Określa, czy identyfikator SID właściciela deskryptora zabezpieczeń została ustawiona domyślnie.|  
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|Określa, czy Lista SACL jest skonfigurowany do obsługi automatycznych propagacji.|  
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|Określa, czy domyślnie SACL skonfigurowano deskryptora zabezpieczeń.|  
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|Określa, czy deskryptora zabezpieczeń zawiera listę kontroli dostępu.|  
|[CSecurityDesc::IsSaclProtected](#issaclprotected)|Określa, czy Lista SACL skonfigurowano w celu zapobieżenia modyfikacjom.|  
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|Określa, czy deskryptor zabezpieczeń jest w formacie autorelacyjnym.|  
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|Wywołanie tej metody można przekonwertować deskryptora zabezpieczeń na formacie bezwzględnym.|  
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|Wywołanie tej metody można przekonwertować deskryptora zabezpieczeń na format autorelacyjny.|  
|[CSecurityDesc::SetControl](#setcontrol)|Ustawia bity kontrolne deskryptora zabezpieczeń.|  
|[CSecurityDesc::SetDacl](#setdacl)|Ustawia informacje przy użyciu listy DACL. Jeśli lista DACL dotycząca jest już obecny w deskryptorze zabezpieczeń, zostanie zastąpiony.|  
|[CSecurityDesc::SetGroup](#setgroup)|Ustawia informacje dotyczące grupy podstawowej deskryptora zabezpieczeń formacie bezwzględnym, zastępując wszelkie podstawowe informacje o grupach jeszcze nie istnieje.|  
|[CSecurityDesc::SetOwner](#setowner)|Ustawia informacje o właścicielu deskryptora zabezpieczeń formacie bezwzględnym, zastępując wszelkie informacje o właścicielu jeszcze nie istnieje.|  
|[CSecurityDesc::SetSacl](#setsacl)|Ustawia informacje na liście. Jeśli listę kontroli dostępu jest już obecny w deskryptorze zabezpieczeń, zostanie zastąpiony.|  
|[CSecurityDesc::ToString](#tostring)|Konwertuje format ciągu deskryptora zabezpieczeń.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSecurityDesc::operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|Zwraca wskaźnik do **SECURITY_DESCRIPTOR** struktury.|  
|[CSecurityDesc::operator =](#operator_eq)|Operator przypisania.|  
  
## <a name="remarks"></a>Uwagi  
 **SECURITY_DESCRIPTOR** struktura zawiera informacje dotyczące zabezpieczeń, skojarzona z obiektem. Ta struktura jest używana przez aplikacje i zbadać stan zabezpieczeń obiektu. Zobacz też [AtlGetSecurityDescriptor](security-global-functions.md#atlgetsecuritydescriptor).  
  
 Aplikacje nie należy modyfikować **SECURITY_DESCRIPTOR** struktury bezpośrednio, a zamiast tego należy użyć metody klasy udostępniane.  
  
 Aby obejrzeć wprowadzenie do modelu kontroli dostępu w systemie Windows, temacie [kontroli dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374860) w zestawie Windows SDK.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h  
  
##  <a name="csecuritydesc"></a>CSecurityDesc::CSecurityDesc  
 Konstruktor.  
  
```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );  
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 `CSecurityDesc` Obiektu lub **SECURITY_DESCRIPTOR** struktury można przypisać do nowego `CSecurityDesc` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 `CSecurityDesc` Można opcjonalnie można utworzyć obiektu przy użyciu **SECURITY_DESCRIPTOR** struktury lub wcześniej zdefiniowanego `CSecurityDesc` obiektu.  
  
##  <a name="dtor"></a>CSecurityDesc:: ~ CSecurityDesc  
 Destruktor.  
  
```
virtual ~CSecurityDesc() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Destruktor zwalnia wszystkie przydzielone zasoby.  
  
##  <a name="fromstring"></a>CSecurityDesc::FromString  
 Konwertuje deskryptora zabezpieczeń format ciągu deskryptora zabezpieczeń prawidłowy, funkcjonalności.  
  
```
bool FromString(LPCTSTR pstr) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pstr`  
 Wskaźnik do zerem ciąg, który zawiera [format ciągu deskryptora zabezpieczeń](http://msdn.microsoft.com/library/windows/desktop/aa379570) do skonwertowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia. Zgłasza wyjątek w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ciąg można tworzyć przy użyciu [CSecurityDesc::ToString](#tostring). Konwersja deskryptora zabezpieczeń na ciąg ułatwia do przechowywania i transmisji.  
  
 Ta metoda jest dostępna tylko w systemie Windows 2000 lub nowszy ponieważ wywołuje [ConvertStringSecurityDescriptorToSecurityDescriptor](http://msdn.microsoft.com/library/windows/desktop/aa376401).  
  
##  <a name="getcontrol"></a>CSecurityDesc::GetControl  
 Pobiera kontrolować informacji z deskryptora zabezpieczeń.  
  
```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *psdc*  
 Wskaźnik do **SECURITY_DESCRIPTOR_CONTROL** struktury, która otrzymuje informacje dotyczące sterowania deskryptora zabezpieczeń.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli metoda zakończy się powodzeniem, wartość false w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest tylko przydatne w przypadku korzystania z systemu Windows 2000 lub nowszym, ponieważ wywołuje [GetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa446647).  
  
##  <a name="getdacl"></a>CSecurityDesc::GetDacl  
 Pobiera DACL kontroli dostępu (DACL) listy informacji z deskryptora zabezpieczeń.  
  
```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pDacl`  
 Wskaźnik do `CDacl` struktury, w której chcesz przechowywać kopię DACL deskryptora zabezpieczeń. Jeśli DACL **listy ACL** istnieje, Ustawia metodę `pDacl` adres zabezpieczeń elementu DACL deskryptora **listy ACL**. Jeśli DACL **ACL** nie istnieje, wartość nie jest przechowywana.  
  
 `pbPresent`  
 Wskaźnik do wartości, który wskazuje na obecność DACL **ACL** w podany deskryptor zabezpieczeń. Jeśli deskryptora zabezpieczeń zawiera DACL **ACL**, ten parametr ma wartość true. Jeśli deskryptora zabezpieczeń nie zawiera DACL **ACL**, ten parametr ma wartość false.  
  
 `pbDefaulted`  
 Wskaźnik do flagę ustawioną wartość flagi SE_DACL_DEFAULTED w **SECURITY_DESCRIPTOR_CONTROL** struktury Jeśli DACL **ACL** istnieje dla deskryptora zabezpieczeń. Jeśli ta flaga ma wartość true, DACL **ACL** została pobrana przez domyślnego mechanizmu; w przypadku wartości FAŁSZ DACL **ACL** został jawnie określony przez użytkownika.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli metoda zakończy się powodzeniem, wartość false w przypadku niepowodzenia.  
  
##  <a name="getgroup"></a>CSecurityDesc::GetGroup  
 Pobiera informacje o podstawowej grupy z deskryptora zabezpieczeń.  
  
```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pSid`  
 Wskaźnik do [CSid](../../atl/reference/csid-class.md) (identyfikator zabezpieczeń) odbierająca kopię grupy przechowywane w CDacl.  
  
 `pbDefaulted`  
 Wskaźnik do flagę ustawioną wartość flagi SE_GROUP_DEFAULTED w **SECURITY_DESCRIPTOR_CONTROL** struktury, gdy metoda zwróci wartość.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli metoda zakończy się powodzeniem, wartość false w przypadku niepowodzenia.  
  
##  <a name="getowner"></a>CSecurityDesc::GetOwner  
 Pobiera informacje właściciela z deskryptora zabezpieczeń.  
  
```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pSid`  
 Wskaźnik do [CSid](../../atl/reference/csid-class.md) (identyfikator zabezpieczeń) odbierająca kopię grupy przechowywane w CDacl.  
  
 `pbDefaulted`  
 Wskaźnik do flagę ustawioną wartość flagi SE_OWNER_DEFAULTED w **SECURITY_DESCRIPTOR_CONTROL** struktury, gdy metoda zwróci wartość.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli metoda zakończy się powodzeniem, wartość false w przypadku niepowodzenia.  
  
##  <a name="getpsecurity_descriptor"></a>CSecurityDesc::GetPSECURITY_DESCRIPTOR  
 Zwraca wskaźnik do **SECURITY_DESCRIPTOR** struktury.  
  
```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do [SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561) struktury.  
  
##  <a name="getsacl"></a>CSecurityDesc::GetSacl  
 Pobiera informacje o systemie kontroli dostępu (SACL) listy z deskryptora zabezpieczeń.  
  
```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pSacl`  
 Wskaźnik do `CSacl` struktury, w której chcesz przechowywać kopię SACL deskryptora zabezpieczeń. Jeśli system **listy ACL** istnieje, Ustawia metodę `pSacl` adres deskryptora zabezpieczeń systemu **ACL**. Jeśli system **ACL** nie istnieje, wartość nie jest przechowywana.  
  
 `pbPresent`  
 Wskaźnik do flagę metody ustawia obecności systemu **ACL** w podany deskryptor zabezpieczeń. Jeśli system zawiera deskryptora zabezpieczeń **ACL**, ten parametr ma wartość true. Jeśli deskryptora zabezpieczeń nie zawiera systemu **ACL**, ten parametr ma wartość false.  
  
 `pbDefaulted`  
 Wskaźnik do flagę ustawioną wartość flagi SE_SACL_DEFAULTED w **SECURITY_DESCRIPTOR_CONTROL** struktury, jeśli system **ACL** istnieje dla deskryptora zabezpieczeń.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli metoda zakończy się powodzeniem, wartość false w przypadku niepowodzenia.  
  
##  <a name="isdaclautoinherited"></a>CSecurityDesc::IsDaclAutoInherited  
 Określa, jeśli lista DACL kontroli dostępu (DACL) jest skonfigurowany do obsługi automatycznych propagacji.  
  
```
bool IsDaclAutoInherited() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli deskryptora zabezpieczeń zawiera listy DACL, który jest skonfigurowany do obsługi automatycznego propagacji zapisów dziedziczne kontroli dostępu (ACE) do istniejących obiektów podrzędnych. W przeciwnym razie zwraca wartość false.  
  
### <a name="remarks"></a>Uwagi  
 System ustawia ten bit podczas wykonywania algorytm automatycznego dziedziczenia dla obiekt i jego istniejących obiektów podrzędnych.  
  
##  <a name="isdacldefaulted"></a>CSecurityDesc::IsDaclDefaulted  
 Określa, czy deskryptor zabezpieczeń jest skonfigurowane z domyślnej listy DACL kontroli dostępu (DACL).  
  
```
bool IsDaclDefaulted() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli deskryptora zabezpieczeń zawiera domyślne listy DACL, wartość false w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Ta flaga może mieć wpływ na sposób system traktuje listy DACL względem dziedziczenia wpisu kontroli dostępu. Na przykład jeśli twórcy obiektów nie określa listy DACL, obiekt odbiera domyślnej listy DACL z twórcy tokenu dostępu. System zignoruje tej flagi, jeśli nie ustawiono flagi SE_DACL_PRESENT.  
  
 Ta flaga służy do określania, jak jest końcowego DACL na obiekt ma zostać obliczony, a nie znajduje się fizycznie w formancie deskryptora zabezpieczeń zabezpieczanego obiektu.  
  
 Aby ustawić tę flagę, użyj [CSecurityDesc::SetDacl](#setdacl) metody.  
  
##  <a name="isdaclpresent"></a>CSecurityDesc::IsDaclPresent  
 Określa, czy deskryptora zabezpieczeń zawiera listy DACL kontroli dostępu (DACL).  
  
```
bool IsDaclPresent() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli deskryptora zabezpieczeń zawiera listy DACL, wartość false w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ta flaga nie jest ustawiona, lub jeśli ta flaga jest ustawiona, a listy DACL ma wartość NULL, deskryptora zabezpieczeń umożliwia uzyskanie pełnego dostępu dla wszystkich użytkowników.  
  
 Ta flaga jest wykorzystywana do przechowywania informacji o zabezpieczeniach określone przez obiekt wywołujący, dopóki deskryptor zabezpieczeń jest skojarzony z zabezpieczanego obiektu. Po deskryptor zabezpieczeń jest skojarzony z zabezpieczanego obiektu, zawsze ustawiona flaga SE_DACL_PRESENT w formancie deskryptora zabezpieczeń.  
  
 Aby ustawić tę flagę, użyj [CSecurityDesc::SetDacl](#setdacl) metody.  
  
##  <a name="isdaclprotected"></a>CSecurityDesc::IsDaclProtected  
 Określa, czy lista DACL kontroli dostępu (DACL) jest skonfigurowany do uniemożliwiają zmiany.  
  
```
bool IsDaclProtected() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli skonfigurowano listy DACL deskryptora zabezpieczeń uniemożliwić modyfikowany przez wpisy dziedziczne kontroli dostępu (ACE). W przeciwnym razie zwraca wartość false.  
  
### <a name="remarks"></a>Uwagi  
 Aby ustawić tę flagę, użyj [CSecurityDesc::SetDacl](#setdacl) metody.  
  
 Ta metoda jest znaczący tylko w systemie Windows 2000 lub nowszym, automatyczne propagacji dziedziczne ACE obsługuje tylko system Windows 2000.  
  
##  <a name="isgroupdefaulted"></a>CSecurityDesc::IsGroupDefaulted  
 Określa, czy identyfikator zabezpieczeń grupy deskryptora zabezpieczeń (SID) została ustawiona domyślnie.  
  
```
bool IsGroupDefaulted() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true Jeśli domyślnego mechanizmu zamiast oryginalnej dostawcy deskryptora zabezpieczeń Podany deskryptor zabezpieczeń identyfikator SID grupy. W przeciwnym razie zwraca wartość false.  
  
### <a name="remarks"></a>Uwagi  
 Aby ustawić tę flagę, użyj [CSecurityDesc::SetGroup](#setgroup) metody.  
  
##  <a name="isownerdefaulted"></a>CSecurityDesc::IsOwnerDefaulted  
 Określa, czy identyfikator zabezpieczeń właściciela deskryptora zabezpieczeń (SID) została ustawiona domyślnie.  
  
```
bool IsOwnerDefaulted() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli domyślny mechanizm zamiast oryginalnej dostawcy deskryptora zabezpieczeń podany identyfikator SID właściciela deskryptora zabezpieczeń. W przeciwnym razie zwraca wartość false.  
  
### <a name="remarks"></a>Uwagi  
 Aby ustawić tę flagę, użyj [CSecurityDesc::SetOwner](#setowner) metody.  
  
##  <a name="issaclautoinherited"></a>CSecurityDesc::IsSaclAutoInherited  
 Określa, jeśli system listy kontroli dostępu (SACL) jest skonfigurowany do obsługi automatycznych propagacji.  
  
```
bool IsSaclAutoInherited() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli deskryptora zabezpieczeń zawiera listę kontroli dostępu, który jest skonfigurowany do obsługi automatycznego propagacji zapisów dziedziczne kontroli dostępu (ACE) do istniejących obiektów podrzędnych. W przeciwnym razie zwraca wartość false.  
  
### <a name="remarks"></a>Uwagi  
 System ustawia ten bit podczas wykonywania algorytm automatycznego dziedziczenia dla obiekt i jego istniejących obiektów podrzędnych.  
  
##  <a name="issacldefaulted"></a>CSecurityDesc::IsSaclDefaulted  
 Określa, czy deskryptora zabezpieczeń jest skonfigurowany z domyślnej listy kontroli dostępu do systemu (SACL).  
  
```
bool IsSaclDefaulted() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli deskryptora zabezpieczeń zawiera domyślne SACL, wartość false w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Ta flaga może mieć wpływ na sposób system traktuje SACL, względem dziedziczenia wpisu kontroli dostępu. System zignoruje tej flagi, jeśli nie ustawiono flagi SE_SACL_PRESENT.  
  
 Aby ustawić tę flagę, użyj [CSecurityDesc::SetSacl](#setsacl) metody.  
  
##  <a name="issaclpresent"></a>CSecurityDesc::IsSaclPresent  
 Określa, czy deskryptora zabezpieczeń zawiera listę kontroli dostępu (SACL) systemu.  
  
```
bool IsSaclPresent() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli deskryptora zabezpieczeń zawiera listę kontroli dostępu, wartość false w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Aby ustawić tę flagę, użyj [CSecurityDesc::SetSacl](#setsacl) metody.  
  
##  <a name="issaclprotected"></a>CSecurityDesc::IsSaclProtected  
 Określa, czy system listy kontroli dostępu (SACL) jest skonfigurowany do uniemożliwiają zmiany.  
  
```
bool IsSaclProtected() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli Lista SACL jest skonfigurowany do deskryptora zabezpieczeń uniemożliwić modyfikowany przez wpisy dziedziczne kontroli dostępu (ACE). W przeciwnym razie zwraca wartość false.  
  
### <a name="remarks"></a>Uwagi  
 Aby ustawić tę flagę, użyj [CSecurityDesc::SetSacl](#setsacl) metody.  
  
 Ta metoda jest znaczący tylko w systemie Windows 2000 lub nowszym, automatyczne propagacji dziedziczne ACE obsługuje tylko system Windows 2000.  
  
##  <a name="isselfrelative"></a>CSecurityDesc::IsSelfRelative  
 Określa, czy deskryptor zabezpieczeń jest w formacie autorelacyjnym.  
  
```
bool IsSelfRelative() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli deskryptor zabezpieczeń jest w formacie autorelacyjnym wszystkie informacje zabezpieczeń ciągłego bloku pamięci. Zwraca wartość false, jeśli deskryptor zabezpieczeń jest w formacie bezwzględnym. Aby uzyskać więcej informacji, zobacz [bezwzględnym i deskryptorów zabezpieczeń Self-Relative](http://msdn.microsoft.com/library/windows/desktop/aa374807).  
  
##  <a name="makeabsolute"></a>CSecurityDesc::MakeAbsolute  
 Wywołanie tej metody można przekonwertować deskryptora zabezpieczeń na formacie bezwzględnym.  
  
```
bool MakeAbsolute() throw(...);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli metoda zakończy się powodzeniem, wartość false w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Deskryptor zabezpieczeń w formacie bezwzględnym podano łącza do informacji, które zawiera, zamiast samych informacji. Deskryptor zabezpieczeń w formacie autorelacyjnym zawiera informacje w ciągłego bloku pamięci. W deskryptorze zabezpieczeń autorelacyjnym **SECURITY_DESCRIPTOR** struktury zawsze uruchamia informacje, ale deskryptora zabezpieczeń obiektu innych składników może być zgodny ze strukturą w dowolnej kolejności. Zamiast używać adresów pamięci, składniki deskryptora zabezpieczeń autorelacyjnym są identyfikowane przez przesunięcia od początku deskryptora zabezpieczeń. Ten format jest przydatne, gdy deskryptor zabezpieczeń muszą być przechowywane na dysku lub przesyłane przy użyciu protokołu komunikacji. Aby uzyskać więcej informacji, zobacz [bezwzględnym i deskryptorów zabezpieczeń Self-Relative](http://msdn.microsoft.com/library/windows/desktop/aa374807).  
  
##  <a name="makeselfrelative"></a>CSecurityDesc::MakeSelfRelative  
 Wywołanie tej metody można przekonwertować deskryptora zabezpieczeń na format autorelacyjny.  
  
```
bool MakeSelfRelative() throw(...);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli metoda zakończy się powodzeniem, wartość false w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Deskryptor zabezpieczeń w formacie bezwzględnym podano łącza do informacji, które zawiera, a nie samych informacji. Deskryptor zabezpieczeń w formacie autorelacyjnym zawiera informacje w ciągłego bloku pamięci. W deskryptorze zabezpieczeń autorelacyjnym **SECURITY_DESCRIPTOR** struktury zawsze uruchamia informacje, ale deskryptora zabezpieczeń obiektu innych składników może być zgodny ze strukturą w dowolnej kolejności. Zamiast używać adresów pamięci, składniki deskryptora zabezpieczeń są identyfikowane przez przesunięcia od początku deskryptora zabezpieczeń. Ten format jest przydatne, gdy deskryptor zabezpieczeń muszą być przechowywane na dysku lub przesyłane przy użyciu protokołu komunikacji. Aby uzyskać więcej informacji, zobacz [bezwzględnym i deskryptorów zabezpieczeń Self-Relative](http://msdn.microsoft.com/library/windows/desktop/aa374807).  
  
##  <a name="operator_eq"></a>CSecurityDesc::operator =  
 Operator przypisania.  
  
```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);  
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 **SECURITY_DESCRIPTOR** struktury lub `CSecurityDesc` obiektu można przypisać do `CSecurityDesc` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zaktualizowane `CSecurityDesc` obiektu.  
  
##  <a name="operator_const_security_descriptor__star"></a>CSecurityDesc::operator const SECURITY_DESCRIPTOR *  
 Rzutuje wartość na wskaźnik do **SECURITY_DESCRIPTOR** struktury.  
  
```  
operator const SECURITY_DESCRIPTOR *() const throw();
```  
  
##  <a name="setcontrol"></a>CSecurityDesc::SetControl  
 Ustawia bity kontrolne deskryptora zabezpieczeń.  
  
```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest, 
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ControlBitsOfInterest`  
 A **SECURITY_DESCRIPTOR_CONTROL** maski, która wskazuje liczbę bitów formantu można ustawić. Lista flagi, które można ustawić, zobacz [SetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa379582\(v=vs.85\).aspx).  
  
 `ControlBitsToSet`  
 A `SECURITY_DESCRIPTOR_CONTROL` maski, która wskazuje nowe wartości bitów kontroli określonej `ControlBitsOfInterest` maski. Ten parametr może być kombinacją flag dla `ControlBitsOfInterest` parametru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest dostępna tylko w systemie Windows 2000 lub nowszym, ponieważ wywołuje [SetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa379582\(v=vs.85\).aspx).  
  
##  <a name="setdacl"></a>CSecurityDesc::SetDacl  
 Ustawia informacje o liście DACL kontroli dostępu (DACL). Jeśli lista DACL dotycząca jest już obecny w deskryptorze zabezpieczeń, zostanie zastąpiony.  
  
```
inline void SetDacl(  
    bool bPresent = true,
    bool bDefaulted = false) throw(...);

inline void SetDacl(  
    const CDacl& Dacl,
    bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *Lista DACL*  
 Odwołanie do `CDacl` określenie listy DACL dla deskryptora zabezpieczeń obiektu. Ten parametr nie może mieć wartości NULL. Aby ustawić wartości NULL DACL deskryptora zabezpieczeń, pierwszy formularz metody powinien być używany z `bPresent` ustawiony na wartość false.  
  
 `bPresent`  
 Określa flagi wskazujące na obecność DACL w deskryptora zabezpieczeń. Jeśli ten parametr ma wartość true, metoda ustawia flagę SE_DACL_PRESENT **SECURITY_DESCRIPTOR_CONTROL** struktury i korzysta z wartości w *Dacl* i `bDefaulted` parametrów. Jeśli ma ona wartość false, metoda usuwa flagę SE_DACL_PRESENT i `bDefaulted` jest ignorowana.  
  
 `bDefaulted`  
 Określa flagę wskazującą źródło listy DACL. Jeśli ta flaga ma wartość true, listy DACL pobraniu przez mechanizmu domyślnego. W przypadku wartości FAŁSZ listy DACL został jawnie określony przez użytkownika. Metoda przechowuje tę wartość w Flaga SE_DACL_DEFAULTED **SECURITY_DESCRIPTOR_CONTROL** struktury. Jeśli ten parametr nie jest określony, Flaga SE_DACL_DEFAULTED jest wyczyszczone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Brak istotną różnicą między pustą i nieistniejącą DACL. Gdy lista DACL dotycząca jest pusta, zawiera żadnych wpisów kontroli dostępu i jawnie przyznano żadnych praw dostępu. W związku z tym niejawnie odmówiono dostępu do obiektu. Gdy obiekt nie ma żadnych DACL, z drugiej strony, do obiektu nie przypisano żadnych ochrony i uzyskuje wszystkie żądania dostępu.  
  
##  <a name="setgroup"></a>CSecurityDesc::SetGroup  
 Ustawia informacje dotyczące grupy podstawowej deskryptora zabezpieczeń formacie bezwzględnym, zastępując wszelkie podstawowe informacje o grupach jeszcze nie istnieje.  
  
```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `Sid`  
 Odwołanie do [CSid](../../atl/reference/csid-class.md) obiektu dla nowej grupy podstawowej deskryptora zabezpieczeń. Ten parametr nie może mieć wartości NULL. Deskryptor zabezpieczeń może być oznaczony jako nie ma listy DACL lub listę kontroli dostępu, ale musi mieć grupę i właściciela, nawet te są NULL identyfikatora SID (czyli wbudowane SID o specjalnym znaczeniu).  
  
 `bDefaulted`  
 Wskazuje, czy informacje o podstawowej grupie został utworzony na podstawie domyślnego mechanizmu. Jeśli ta wartość wynosi true, jest domyślne informacje i metody przechowuje tej wartości jako flagi SE_GROUP_DEFAULTED w **SECURITY_DESCRIPTOR_CONTROL** struktury. Jeśli ten parametr ma wartość zero, Flaga SE_GROUP_DEFAULTED jest wyczyszczone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
##  <a name="setowner"></a>CSecurityDesc::SetOwner  
 Ustawia informacje o właścicielu deskryptora zabezpieczeń w formacie bezwzględnym. Zastępuje wszelkie informacje o właścicielu jeszcze nie istnieje.  
  
```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `Sid`  
 [CSid](../../atl/reference/csid-class.md) obiekt podstawowy właściciel nowego deskryptora zabezpieczeń. Ten parametr nie może mieć wartości NULL.  
  
 `bDefaulted`  
 Wskazuje, czy informacje o właścicielu jest określana na podstawie domyślnego mechanizmu. Jeśli ta wartość wynosi true, to domyślne informacje. Metoda przechowuje tej wartości jako flagi SE_OWNER_DEFAULTED w **SECURITY_DESCRIPTOR_CONTROL** struktury. Jeśli ten parametr ma wartość zero, Flaga SE_OWNER_DEFAULTED jest wyczyszczone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
##  <a name="setsacl"></a>CSecurityDesc::SetSacl  
 Ustawia informacje o liście kontroli dostępu do systemu (SACL). Jeśli listę kontroli dostępu jest już obecny w deskryptorze zabezpieczeń, zostanie zastąpiony.  
  
```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *Lista SACL*  
 Wskaźnik do `CSacl` określenie SACL dla deskryptora zabezpieczeń obiektu. Ten parametr nie może mieć wartości NULL i musi być obiektem CSacl. W przeciwieństwie do listy DACL nie ma różnic między NULL ani pusta Lista SACL, ponieważ SACL obiektów należy określać prawa dostępu, tylko informacje dotyczące inspekcji.  
  
 `bDefaulted`  
 Określa flagę wskazującą źródło Lista SACL. Jeśli ta flaga ma wartość true, Lista SACL pobraniu przez mechanizmu domyślnego. W przypadku wartości FAŁSZ Lista SACL został jawnie określony przez użytkownika. Metoda przechowuje tę wartość w Flaga SE_SACL_DEFAULTED **SECURITY_DESCRIPTOR_CONTROL** struktury. Jeśli ten parametr nie jest określony, Flaga SE_SACL_DEFAULTED jest wyczyszczone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
##  <a name="tostring"></a>CSecurityDesc::ToString  
 Konwertuje format ciągu deskryptora zabezpieczeń.  
  
```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pstr`  
 Wskaźnik do zerem ciągu, która otrzyma [format ciągu deskryptora zabezpieczeń](http://msdn.microsoft.com/library/windows/desktop/aa379570).  
  
 `si`  
 Określa kombinację SECURITY_INFORMATION flagi bitów, aby wskazać składniki deskryptora zabezpieczeń, aby uwzględnić w ciągu wyjściowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Po w formacie ciągu deskryptora zabezpieczeń, można łatwiej przechowywane lub przesyłane. Użyj `CSecurityDesc::FromString` do przekonwertowania ciągu do deskryptora zabezpieczeń.  
  
 `si` Parametr może zawierać następujące flagi SECURITY_INFORMATION:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|OWNER_SECURITY_INFORMATION|Obejmować właściciela.|  
|GROUP_SECURITY_INFORMATION|Obejmują grupy podstawowej.|  
|DACL_SECURITY_INFORMATION|Zawierają listy DACL.|  
|SACL_SECURITY_INFORMATION|To Lista SACL.|  
  
 Jeśli w wejściowy deskryptor zabezpieczeń jest ustawiony bit kontroli SE_DACL_PRESENT listy DACL ma wartość NULL, metoda kończy się niepowodzeniem.  
  
 Jeśli nie ustawiono bitu kontroli SE_DACL_PRESENT w deskryptorze zabezpieczeń listy DACL ma wartość NULL, wynikowego ciągu deskryptora zabezpieczeń nie ma składnika D:. Zobacz [Format ciągu deskryptora zabezpieczeń](http://msdn.microsoft.com/library/windows/desktop/aa379570) więcej szczegółów.  
  
 Ta metoda jest dostępna tylko w systemie Windows 2000 lub nowszego oraz jak wywołuje [ConvertStringSecurityDescriptorToSecurityDescriptor](http://msdn.microsoft.com/library/windows/desktop/aa376401).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia — przykład](../../visual-cpp-samples.md)   
 [SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Globalne funkcje zabezpieczeń](../../atl/reference/security-global-functions.md)
