

# endpoints
post
http://0.0.0.0:8000/api/routes/create
{
    "uuid": "550e8400-e29b-41d4-a716-446655440000",
    "name": "Ruta Centro",
    "description": "Entrega a clientes premium",
    "date": "2025-05-15",
    "start_time": "08:30",  // Hora en formato 24H
    "end_time": "12:00",
    "vehicle_plate": "ABC-123",
    "driver_jwt": "eyJhbG...", // Opcional
    "driver_info_cache": {"nombre": "Juan Pérez"} // Opcional
}

respuesta esperada
Validating route data{"message":"Route created successfully","data":{"name":"Ruta Centro","description":"Entrega a
clientes
premium","date":"2025-05-15T00:00:00.000000Z","start_time":"2025-05-13T08:30:00.000000Z","end_time":"2025-05-13T12:00:00.000000Z","vehicle_plate":"ABC-123","uuid":"c332aad2-f26f-46eb-848e-55fb87655f70","updated_at":"2025-05-13T03:40:47.000000Z","created_at":"2025-05-13T03:40:47.000000Z","id":3}}

post
http://0.0.0.0:8000/api/delivery/create

{
  "route_id": 1,
  "recipient_name": "María González",
  "recipient_phone": "5551234567",
  "recipient_address": "Av. Principal 123, Col. Centro",
  "package_weight": 2.5,
  "package_description": "Paquete con documentos legales",
  "scheduled_at": "2023-12-15 14:00:00",
  "delivery_instructions": "Entregar en recepción, preguntar por Sra. Pérez",
  "status_code": "PROCESSING"
}

respuesta esperada
Validating delivery data{"success":true,"message":"Delivery created
successfully","data":{"route_id":3,"recipient_name":"Mar\u00eda
Gonz\u00e1lez","recipient_phone":"5551234567","recipient_address":"Av. Principal 123, Col.
Centro","package_weight":2.5,"package_description":"Paquete con documentos
legales","scheduled_at":"2023-12-15T14:00:00.000000Z","delivery_instructions":"Entregar en recepci\u00f3n, preguntar por
Sra.
P\u00e9rez","status_id":2,"tracking_number":"DEL-6822BF9B8EB74","updated_at":"2025-05-13T03:42:19.000000Z","created_at":"2025-05-13T03:42:19.000000Z","id":2}}

get
http://0.0.0.0:8000/api/delivery
rspuesta esperada 
{
    "success": true,
    "data": {
        "current_page": 1,
        "data": [
            {
                "id": 2,
                "route_id": 3,
                "status_id": 2,
                "tracking_number": "DEL-6822BF9B8EB74",
                "recipient_name": "María González",
                "recipient_phone": "5551234567",
                "recipient_address": "Av. Principal 123, Col. Centro",
                "delivery_instructions": "Entregar en recepción, preguntar por Sra. Pérez",
                "package_weight": "2.50",
                "package_description": "Paquete con documentos legales",
                "scheduled_at": "2023-12-15T14:00:00.000000Z",
                "delivered_at": null,
                "delivery_proof": null,
                "created_at": "2025-05-13T03:42:19.000000Z",
                "updated_at": "2025-05-13T03:42:19.000000Z",
                "route": {
                    "id": 3,
                    "uuid": "c332aad2-f26f-46eb-848e-55fb87655f70",
                    "name": "Ruta Centro",
                    "driver_jwt": null,
                    "driver_info_cache": null,
                    "description": "Entrega a clientes premium",
                    "date": "2025-05-15T00:00:00.000000Z",
                    "start_time": "2025-05-13T08:30:00.000000Z",
                    "end_time": "2025-05-13T12:00:00.000000Z",
                    "vehicle_plate": "ABC-123",
                    "created_at": "2025-05-13T03:40:47.000000Z",
                    "updated_at": "2025-05-13T03:40:47.000000Z"
                },
                "status": {
                    "id": 2,
                    "code": "PROCESSING",
                    "name": "En preparación",
                    "color": "#1E90FF",
                    "description": "Preparando paquete para envío",
                    "is_active": true,
                    "created_at": "2025-05-13T01:17:32.000000Z",
                    "updated_at": "2025-05-13T01:17:32.000000Z"
                }
            }
        ],
        "first_page_url": "http://0.0.0.0:8000/api/delivery?page=1",
        "from": 1,
        "last_page": 1,
        "last_page_url": "http://0.0.0.0:8000/api/delivery?page=1",
        "links": [
            {
                "url": null,
                "label": "&laquo; Previous",
                "active": false
            },
            {
                "url": "http://0.0.0.0:8000/api/delivery?page=1",
                "label": "1",
                "active": true
            },
            {
                "url": null,
                "label": "Next &raquo;",
                "active": false
            }
        ],
        "next_page_url": null,
        "path": "http://0.0.0.0:8000/api/delivery",
        "per_page": 10,
        "prev_page_url": null,
        "to": 1,
        "total": 1
    }
}