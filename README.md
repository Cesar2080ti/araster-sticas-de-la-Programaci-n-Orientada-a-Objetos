# Definición de la clase Cliente
class Cliente:
    def __init__(self, nombre, correo):
        """
        Constructor de la clase Cliente.
        :param nombre: Nombre del cliente.
        :param correo: Correo electrónico del cliente.
        """
        self.nombre = nombre
        self.correo = correo

    def __str__(self):
        """
        Representación en cadena del cliente.
        :return: Una cadena con el nombre y correo del cliente.
        """
        return f"{self.nombre} ({self.correo})"


# Definición de la clase Hotel
class Hotel:
    def __init__(self, nombre, ubicacion, habitaciones_totales):
        """
        Constructor de la clase Hotel.
        :param nombre: Nombre del hotel.
        :param ubicacion: Ubicación del hotel.
        :param habitaciones_totales: Número total de habitaciones disponibles.
        """
        self.nombre = nombre
        self.ubicacion = ubicacion
        self.habitaciones_totales = habitaciones_totales
        self.habitaciones_disponibles = habitaciones_totales  # Asumimos que todas las habitaciones están disponibles al inicio

    def realizar_reserva(self, cliente, num_habitaciones):
        """
        Realiza una reserva para un cliente si hay habitaciones disponibles.
        :param cliente: Cliente que realiza la reserva.
        :param num_habitaciones: Número de habitaciones a reservar.
        :return: Mensaje indicando si la reserva fue exitosa o no.
        """
        if num_habitaciones <= self.habitaciones_disponibles:
            self.habitaciones_disponibles -= num_habitaciones
            return f"Reserva exitosa para {cliente}. {num_habitaciones} habitaciones reservadas."
        else:
            return f"No hay suficientes habitaciones disponibles. Solo quedan {self.habitaciones_disponibles} habitaciones."


# Definición de la clase Reserva
class Reserva:
    def __init__(self, cliente, hotel, num_habitaciones):
        """
        Constructor de la clase Reserva.
        :param cliente: Cliente que realiza la reserva.
        :param hotel: Hotel donde se realiza la reserva.
        :param num_habitaciones: Número de habitaciones reservadas.
        """
        self.cliente = cliente
        self.hotel = hotel
        self.num_habitaciones = num_habitaciones
        self.estado_reserva = hotel.realizar_reserva(cliente, num_habitaciones)

    def mostrar_reserva(self):
        """
        Muestra la información de la reserva.
        :return: Información de la reserva.
        """
        return f"Reserva realizada por {self.cliente}. Hotel: {self.hotel.nombre}, Habitaciones reservadas: {self.num_habitaciones}. Estado: {self.estado_reserva}"


# Ejemplo de uso
if __name__ == "__main__":
    cliente1 = Cliente("Juan Pérez", "juan.perez@email.com")
    hotel1 = Hotel("Hotel Playa", "Cancún", 100)

    # Realizamos una reserva
    reserva1 = Reserva(cliente1, hotel1, 5)

    # Mostramos la información de la reserva
    print(reserva1.mostrar_reserva())
