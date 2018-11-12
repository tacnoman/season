<template>
  <div id="map" />
</template>

<style>
#map {
  width: 100%;
  height: 100% !important;
  left: 0;
  top: 0;
  position: fixed !important;
  pointer-events: none;
  z-index: 0;
}
</style>

<script>
if (process.browser) {
  const awaitMaps = async () =>
    new Promise((resolve, reject) => {
      let counter = 0
      const existMaps = () => {
        if (google && google.maps && google.maps.Map) {
          return resolve()
        }

        counter++
        if (counter > 100) return
        setTimeout(() => existMaps, 200)
      }

      existMaps()
    })

  const run = async () => {
    await awaitMaps()
    window.map = new google.maps.Map(document.getElementById('map'), {
      center: { lat: -34.397, lng: 150.644 },
      disableDefaultUI: true,
      zoom: 8,
      styles: [
        {
          featureType: 'all',
          elementType: 'labels.text.fill',
          stylers: [
            {
              saturation: 36
            },
            {
              color: '#000000'
            },
            {
              lightness: 40
            }
          ]
        },
        {
          featureType: 'all',
          elementType: 'labels.text.stroke',
          stylers: [
            {
              visibility: 'on'
            },
            {
              color: '#000000'
            },
            {
              lightness: 16
            }
          ]
        },
        {
          featureType: 'all',
          elementType: 'labels.icon',
          stylers: [
            {
              visibility: 'off'
            }
          ]
        },
        {
          featureType: 'administrative',
          elementType: 'geometry.fill',
          stylers: [
            {
              color: '#000000'
            },
            {
              lightness: 20
            }
          ]
        },
        {
          featureType: 'administrative',
          elementType: 'geometry.stroke',
          stylers: [
            {
              color: '#000000'
            },
            {
              lightness: 17
            },
            {
              weight: 1.2
            }
          ]
        },
        {
          featureType: 'landscape',
          elementType: 'geometry',
          stylers: [
            {
              color: '#000000'
            },
            {
              lightness: 20
            }
          ]
        },
        {
          featureType: 'poi',
          elementType: 'geometry',
          stylers: [
            {
              color: '#000000'
            },
            {
              lightness: 21
            }
          ]
        },
        {
          featureType: 'road.highway',
          elementType: 'geometry.fill',
          stylers: [
            {
              color: '#000000'
            },
            {
              lightness: 17
            }
          ]
        },
        {
          featureType: 'road.highway',
          elementType: 'geometry.stroke',
          stylers: [
            {
              color: '#000000'
            },
            {
              lightness: 29
            },
            {
              weight: 0.2
            }
          ]
        },
        {
          featureType: 'road.arterial',
          elementType: 'geometry',
          stylers: [
            {
              color: '#000000'
            },
            {
              lightness: 18
            }
          ]
        },
        {
          featureType: 'road.local',
          elementType: 'geometry',
          stylers: [
            {
              color: '#000000'
            },
            {
              lightness: 16
            }
          ]
        },
        {
          featureType: 'transit',
          elementType: 'geometry',
          stylers: [
            {
              color: '#000000'
            },
            {
              lightness: 19
            }
          ]
        },
        {
          featureType: 'water',
          elementType: 'geometry',
          stylers: [
            {
              color: '#000000'
            },
            {
              lightness: 17
            }
          ]
        }
      ]
    })
  }

  run()
}

export default {}
</script>
