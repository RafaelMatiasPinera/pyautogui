# pyautogui
scripts para automatizar mouse y teclado

----------------------------------------------------------------------
import pyautogui
import time

def get_screen_size():
    return pyautogui.size()

def scale_coordinates(coord, original_size, current_size):
    x_scale = current_size[0] / original_size[0]
    y_scale = current_size[1] / original_size[1]
    return (int(coord[0] * x_scale), int(coord[1] * y_scale))

#Configuración original (por ejemplo, para un monitor 1920x1080)
original_size = (1920, 1080)

#Obtener el tamaño actual de la pantalla
current_size = get_screen_size()

#Lista de coordenadas donde queremos hacer clic
#Formato: (x, y, tiempo_espera)
coordenadas = [
    (121, 1059, 2),
    (568, 89 , 2),
]

#Dar tiempo para cambiar a la ventana deseada
print("Cambia a la ventana deseada. Comenzando en 2 segundos...")
time.sleep(2)

#Realizar los clics
for x, y, espera in coordenadas:
    scaled_x, scaled_y = scale_coordinates((x, y), original_size, current_size)
    pyautogui.click(scaled_x, scaled_y)
    print(f"Clic en ({scaled_x}, {scaled_y})")
    time.sleep(espera)


#Simular la escritura de un texto
pyautogui.write('Hola, esto es un texto simulado!', interval=0.05)

#Simular la pulsación de la tecla Enter
pyautogui.press('enter')

print("Secuencia de clics completada")


----------------------------------------------------------------------

import pyautogui
import time

print("Mover el mouse a la posición deseada...")
print("Presiona Ctrl + C para detener el programa y obtener las coordenadas.")

try:
    while True:
        # Obtener la posición actual del mouse
        x, y = pyautogui.position()
        print(f"Coordenadas del mouse: ({x}, {y})", end='\r')
        time.sleep(0.1)  # Pausa breve para no saturar la salida
except KeyboardInterrupt:
    print("\nPrograma detenido.")
    print(f"Últimas coordenadas del mouse: ({x}, {y})")
