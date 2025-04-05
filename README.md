import datetime

class ChemicalSafetyDataSheet:
    """Class to represent and display a Chemical Safety Data Sheet (SDS)"""
    
    def __init__(self, name, cas_number, formula, molecular_weight):
        """Initialize with basic chemical identification"""
        self.name = name
        self.cas_number = cas_number
        self.formula = formula
        self.molecular_weight = molecular_weight
        self.sections = {}
        self.creation_date = datetime.datetime.now().strftime("%Y-%m-%d")
        
    def add_section(self, section_number, section_title, content):
        """Add a section to the SDS"""
        self.sections[section_number] = {
            'title': section_title,
            'content': content
        }
    
    def display_sds(self):
        """Print the complete safety data sheet"""
        print("\n" + "="*80)
        print(f"SAFETY DATA SHEET: {self.name}")
        print("="*80)
        print(f"Creation Date: {self.creation_date}")
        print(f"Chemical Formula: {self.formula}")
        print(f"CAS Number: {self.cas_number}")
        print(f"Molecular Weight: {self.molecular_weight} g/mol")
        print("="*80 + "\n")
        
        # Print all sections in order
        for section_num in sorted(self.sections.keys()):
            section = self.sections[section_num]
            print(f"SECTION {section_num}: {section['title']}")
            print("-"*80)
            for key, value in section['content'].items():
                if isinstance(value, list):
                    print(f"{key}:")
                    for item in value:
                        print(f"  - {item}")
                else:
                    print(f"{key}: {value}")
            print("\n")

# Create SDS for three different chemicals
def create_sample_sds():
    # 1. Sodium Hydroxide (NaOH)
    naoh = ChemicalSafetyDataSheet(
        "Sodium Hydroxide", 
        "1310-73-2", 
        "NaOH", 
        40.00
    )
    
    naoh.add_section(1, "Identification", {
        "Product Name": "Sodium Hydroxide",
        "Synonyms": ["Caustic Soda", "Lye", "Sodium Hydrate"],
        "Recommended Use": "Laboratory chemicals, manufacturing of substances",
        "Supplier": "Chemical Safety Corp.",
        "Emergency Phone": "+1-800-424-9300"
    })
    
    naoh.add_section(2, "Hazard Identification", {
        "Classification": "Corrosive to metals (Category 1), Skin corrosion (Category 1A), Serious eye damage (Category 1)",
        "Signal Word": "DANGER",
        "Hazard Statements": [
            "H290: May be corrosive to metals",
            "H314: Causes severe skin burns and eye damage"
        ],
        "Precautionary Statements": [
            "P260: Do not breathe dust or mist",
            "P280: Wear protective gloves/protective clothing/eye protection/face protection",
            "P301+P330+P331: IF SWALLOWED: Rinse mouth. Do NOT induce vomiting",
            "P303+P361+P353: IF ON SKIN: Remove/Take off immediately all contaminated clothing. Rinse skin with water/shower",
            "P305+P351+P338: IF IN EYES: Rinse cautiously with water for several minutes. Remove contact lenses, if present and easy to do. Continue rinsing"
        ]
    })
    
    naoh.add_section(3, "First Aid Measures", {
        "General Advice": "Consult a physician. Show this safety data sheet to the doctor in attendance.",
        "If Inhaled": "Move person to fresh air. If not breathing, give artificial respiration. Consult a physician.",
        "In Case of Skin Contact": "Take off contaminated clothing immediately. Wash off with soap and plenty of water. Consult a physician.",
        "In Case of Eye Contact": "Rinse thoroughly with plenty of water for at least 15 minutes and consult a physician.",
        "If Swallowed": "Do NOT induce vomiting. Never give anything by mouth to an unconscious person. Rinse mouth with water. Consult a physician."
    })
    
    # 2. Acetone
    acetone = ChemicalSafetyDataSheet(
        "Acetone", 
        "67-64-1", 
        "C₃H₆O", 
        58.08
    )
    
    acetone.add_section(1, "Identification", {
        "Product Name": "Acetone",
        "Synonyms": ["2-Propanone", "Dimethyl ketone", "Propanone"],
        "Recommended Use": "Laboratory chemicals, solvent, paint thinner",
        "Supplier": "Chemical Safety Corp.",
        "Emergency Phone": "+1-800-424-9300"
    })
    
    acetone.add_section(2, "Hazard Identification", {
        "Classification": "Flammable liquids (Category 2), Eye irritation (Category 2A), Specific target organ toxicity - single exposure (Category 3)",
        "Signal Word": "DANGER",
        "Hazard Statements": [
            "H225: Highly flammable liquid and vapor",
            "H319: Causes serious eye irritation",
            "H336: May cause drowsiness or dizziness"
        ],
        "Precautionary Statements": [
            "P210: Keep away from heat/sparks/open flames/hot surfaces. No smoking.",
            "P233: Keep container tightly closed.",
            "P240: Ground/bond container and receiving equipment.",
            "P280: Wear protective gloves/protective clothing/eye protection/face protection.",
            "P305+P351+P338: IF IN EYES: Rinse cautiously with water for several minutes. Remove contact lenses, if present and easy to do. Continue rinsing."
        ]
    })
    
    acetone.add_section(3, "First Aid Measures", {
        "General Advice": "Consult a physician. Show this safety data sheet to the doctor in attendance.",
        "If Inhaled": "Move person to fresh air. If not breathing, give artificial respiration. Consult a physician.",
        "In Case of Skin Contact": "Wash off with soap and plenty of water. Consult a physician.",
        "In Case of Eye Contact": "Rinse thoroughly with plenty of water for at least 15 minutes and consult a physician.",
        "If Swallowed": "Do NOT induce vomiting. Never give anything by mouth to an unconscious person. Rinse mouth with water. Consult a physician."
    })
    
    # 3. Sulfuric Acid
    sulfuric_acid = ChemicalSafetyDataSheet(
        "Sulfuric Acid", 
        "7664-93-9", 
        "H₂SO₄", 
        98.08
    )
    
    sulfuric_acid.add_section(1, "Identification", {
        "Product Name": "Sulfuric Acid",
        "Synonyms": ["Oil of vitriol", "Hydrogen sulfate", "Battery acid"],
        "Recommended Use": "Laboratory chemicals, industrial applications, batteries",
        "Supplier": "Chemical Safety Corp.",
        "Emergency Phone": "+1-800-424-9300"
    })
    
    sulfuric_acid.add_section(2, "Hazard Identification", {
        "Classification": "Corrosive to metals (Category 1), Skin corrosion (Category 1A), Serious eye damage (Category 1)",
        "Signal Word": "DANGER",
        "Hazard Statements": [
            "H290: May be corrosive to metals",
            "H314: Causes severe skin burns and eye damage",
            "H318: Causes serious eye damage"
        ],
        "Precautionary Statements": [
            "P260: Do not breathe dust/fume/gas/mist/vapors/spray",
            "P280: Wear protective gloves/protective clothing/eye protection/face protection",
            "P301+P330+P331: IF SWALLOWED: Rinse mouth. Do NOT induce vomiting",
            "P303+P361+P353: IF ON SKIN: Take off immediately all contaminated clothing. Rinse skin with water/shower",
            "P304+P340: IF INHALED: Remove person to fresh air and keep comfortable for breathing",
            "P305+P351+P338: IF IN EYES: Rinse cautiously with water for several minutes. Remove contact lenses, if present and easy to do. Continue rinsing"
        ]
    })
    
    sulfuric_acid.add_section(3, "First Aid Measures", {
        "General Advice": "Consult a physician immediately. Show this safety data sheet to the doctor in attendance.",
        "If Inhaled": "Move person to fresh air. If not breathing, give artificial respiration. Consult a physician immediately.",
        "In Case of Skin Contact": "Take off contaminated clothing and shoes immediately. Wash off with soap and plenty of water. Consult a physician immediately.",
        "In Case of Eye Contact": "Rinse thoroughly with plenty of water for at least 15 minutes and consult a physician immediately.",
        "If Swallowed": "Do NOT induce vomiting. Never give anything by mouth to an unconscious person. Rinse mouth with water. Consult a physician immediately."
    })
    
    return [naoh, acetone, sulfuric_acid]

# Main execution
if __name__ == "__main__":
    chemicals = create_sample_sds()
    
    # Display all safety data sheets
    for chemical in chemicals:
        chemical.display_sds()
