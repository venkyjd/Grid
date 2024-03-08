class EnergyManagementSystem:   
def __init__(self): 
 # Initialize system components      
 self.microcontroller = Microcontroller()     
 self.pv_panel = PVPanel()    
 self.charge_controller = ChargeController()    
 self.battery = Battery()   
 self.bidirectional_system = BidirectionalSystem()   
 self.grid = Grid()    
 self.ac_load_controller = ACLoadController()
def monitor_parameters(self):       # Continuous monitoring of power parameters       
    load_power = self.ac_load_controller.measure_power()       
    grid_power = self.grid.measure_power()       
    pv_power = self.pv_panel.measure_power()       
    return load_power, grid_power, pv_power   
    def load_pv_power_matching(self, load_power, pv_power):      
           # Check if load power requirements are below PV power output      
         if load_power < pv_power:           
               self.microcontroller.activate_relay()  # Divert surplus power towards the load
![image](https://github.com/venkyjd/Grid/assets/100828679/ca25c131-0a10-4218-b592-e484c3132396)
def handle_load_exceeds_pv_power(self, load_power, pv_power):    
       # If load demand surpasses available PV power, switch to grid power        
     if load_power > pv_power:            
             self.bidirectional_system.switch_to_grid()  # Switch power source to grid   
 def battery_management(self):        # Monitor battery charge level        
        battery_charge_level = self.battery.get_charge_level()        # If battery's charge level is critical, connect grid power to recharge       
            if battery_charge_level < Battery.CRITICAL_DEPTH_OF_DISCHARGE:
                                self.charge_controller.connect_grid_to_battery()
def adaptability_and_flexibility(self, solar_irradiance, load_demand):        # Grant access to load and battery during limited solar irradiance       
     if solar_irradiance < Solar.IRRADIANCE_THRESHOLD:       
                    self.bidirectional_system.allow_access_to_load_and_battery()        # Flexibility for customers to use grid power during substantial load        
      if load_demand > Load.LOAD_THRESHOLD:  
          self.bidirectional_system.allow_access_to_grid()   
 def sell_excess_energy_to_grid(self, load_power, pv_power):        # During low load and abundant solar power, sell excess energy to the grid     
      if load_power < pv_power:           
                excess_energy = pv_power - load_power     
                self.grid.sell_energy(excess_energy)
![image](https://github.com/venkyjd/Grid/assets/100828679/62a9178a-5854-473f-8a35-4c1609c0e524)
