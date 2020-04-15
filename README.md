# PMPS-Homework-1
Fakultet elektrotehnike Tuzla - Projektovanje mikroprocesorskih sistema


Potrebno je realizovati 3 - portni mrežni switch korištenjem STM32 F401RETx mikrokontrolera
(Nucleo board). Navedeni switch osigurava mogudnost povezivanja 3 računarska sistema u
jednostavnu LAN (lokalnu računarsku mrežu) korištenjem standardnog serijskog interfejsa (UART).
Komunikacioni switch omoguduje dvosmjerno prenošenje poruka (paketa) između bilo koja dva
računara. Drugačije rečeno, switch prihvati (primi) poruku sa nekog od portova, te na bazi adrese
odredišta prosljeđuje (šalje) tu istu poruku na drugi odnosno željeni port. Toplogija (zvijezda) ove
LAN mreže i struktura poruka je data na slici.

Za adrese računara možete koristiti slijedede:

Računar koji ide na port UART 1 STM32 adresa je 1

Računar koji ide na port UART 2 STM32 adresa je 2

Računar koji ide na port UART6 adresa je 3


Za razvoj aplikacije koristiti STM Cube HAL API za upravljanje UART periferalima:

HAL_UART_Receive_IT(...) ( nonblocking interrupt driven receive)

HAL_UART_Transmit_IT(...) (nonblocking interrupt driven transmit)

Te definisati callback funkcije za UARTs ISR rutine (receive complete i transmit complete events).
Kako STM Cube osigurava samo po jednu callback funkciju za periferal (kojih može biti više)
potrebno je u samim funkcijama identificirati koji periferal poziva funkciju.

void HAL_UART_RxCpltCallback(UART_HandleTypeDef *huart)

{

If (huart->Instance == USART1) {

// receive complete callback za UART 1

}

If (huart->Instance == USART2) {

// callback za UART 2

}

If (huart->Instance == USART6) {

// callback za UART 6

}

}

void HAL_UART_TxCpltCallback(UART_HandleTypeDef *huart)

{

If (huart->Instance == USART1) {

// transmit complete callback za UART 1

}


If (huart->Instance == USART2) {

// callback za UART 2

}

If (huart->Instance == USART6) {

// callback za UART 6

}

## }

