import React, { useState } from 'react';
import { 
  SafeAreaView, 
  ScrollView, 
  Text, 
  View, 
  Image, 
  TouchableOpacity, 
  StyleSheet,
  Modal,
  TextInput,
} from 'react-native';
import { Ionicons } from '@expo/vector-icons';

export default function App() {
  // 12 Categories
  const categories = [
    { id: 1, name: 'Italian', icon: 'pizza', color: '#FF6B6B' },
    { id: 2, name: 'Indian', icon: 'restaurant', color: '#4ECDC4' },
    { id: 3, name: 'Salad', icon: 'leaf', color: '#45B7D1' },
    { id: 4, name: 'Dessert', icon: 'ice-cream', color: '#96CEB4' },
    { id: 5, name: 'Mexican', icon: 'fast-food', color: '#FFA726' },
    { id: 6, name: 'Asian', icon: 'restaurant', color: '#66BB6A' },
    { id: 7, name: 'Breakfast', icon: 'cafe', color: '#AB47BC' },
    { id: 8, name: 'Vegetarian', icon: 'leaf', color: '#26A69A' },
    { id: 9, name: 'Seafood', icon: 'fish', color: '#42A5F5' },
    { id: 10, name: 'BBQ & Grill', icon: 'flame', color: '#EF5350' },
    { id: 11, name: 'Healthy', icon: 'fitness', color: '#7E57C2' },
    { id: 12, name: 'Quick & Easy', icon: 'flash', color: '#FFCA28' },
  ];

  const initialRecipes = [
    {
      id: 1,
      title: 'Spaghetti Carbonara',
      category: 'Italian',
      time: '30 min',
      difficulty: 'Medium',
      servings: 4,
      calories: '450 per serving',
      ingredients: [
        '400g spaghetti',
        '4 large eggs',
        '150g pancetta or bacon',
        '100g parmesan cheese',
        '2 cloves garlic',
        'Fresh black pepper',
        'Salt to taste'
      ],
      instructions: [
        'Bring a large pot of salted water to boil and cook spaghetti according to package directions.',
        'While pasta cooks, chop pancetta into small pieces.',
        'In a bowl, whisk together eggs and grated parmesan cheese.',
        'In a large pan, cook pancetta until crispy. Add minced garlic and cook for 1 minute.',
        'Drain spaghetti, reserving 1 cup of pasta water.',
        'Add hot spaghetti to the pan with pancetta and toss to combine.',
        'Remove from heat and quickly stir in egg mixture, adding pasta water as needed to create creamy sauce.',
        'Season generously with black pepper and serve immediately.'
      ],
      image: 'https://images.unsplash.com/photo-1598866594230-a7c12756260f?w=400&h=300&fit=crop',
      isFavorite: false,
    },
    {
      id: 2,
      title: 'Chicken Tikka Masala',
      category: 'Indian',
      time: '45 min',
      difficulty: 'Medium',
      servings: 4,
      calories: '520 per serving',
      ingredients: [
        '500g chicken breast',
        '1 cup yogurt',
        '2 tbsp tikka masala paste',
        '1 onion, chopped',
        '2 tomatoes, pureed',
        '1 cup cream',
        '3 tbsp oil',
        'Ginger-garlic paste',
        'Spices: cumin, coriander, turmeric'
      ],
      instructions: [
        'Marinate chicken in yogurt and tikka masala paste for 30 minutes.',
        'Heat oil in a pan and cook onions until golden brown.',
        'Add ginger-garlic paste and cook for 2 minutes.',
        'Add tomato puree and cook until oil separates.',
        'Add marinated chicken and cook for 15 minutes.',
        'Add cream and simmer for 10 more minutes.',
        'Garnish with fresh cilantro and serve with naan or rice.'
      ],
      image: 'https://images.unsplash.com/photo-1565557623262-b51c2513a641?w=400&h=300&fit=crop',
      isFavorite: true,
    },
    {
      id: 3,
      title: 'Caesar Salad',
      category: 'Salad',
      time: '15 min',
      difficulty: 'Easy',
      servings: 2,
      calories: '320 per serving',
      ingredients: [
        '1 romaine lettuce head',
        '1 cup croutons',
        '½ cup parmesan cheese',
        '¼ cup Caesar dressing',
        '2 anchovy fillets (optional)',
        '1 lemon',
        'Black pepper'
      ],
      instructions: [
        'Wash and chop romaine lettuce into bite-sized pieces.',
        'Make Caesar dressing by blending anchovies, garlic, lemon juice, and olive oil.',
        'In a large bowl, combine lettuce, croutons, and parmesan.',
        'Add dressing and toss gently to coat.',
        'Season with black pepper and extra parmesan.',
        'Serve immediately.'
      ],
      image: 'https://images.unsplash.com/photo-1546793665-c74683f339c1?w=400&h=300&fit=crop',
      isFavorite: false,
    },
    {
      id: 4,
      title: 'Chocolate Lava Cake',
      category: 'Dessert',
      time: '25 min',
      difficulty: 'Medium',
      servings: 4,
      calories: '480 per serving',
      ingredients: [
        '200g dark chocolate',
        '100g butter',
        '3 eggs',
        '50g sugar',
        '30g flour',
        'Pinch of salt',
        'Vanilla ice cream for serving'
      ],
      instructions: [
        'Preheat oven to 220°C (425°F).',
        'Melt chocolate and butter together in a double boiler.',
        'In a separate bowl, whisk eggs and sugar until pale and fluffy.',
        'Fold melted chocolate into egg mixture.',
        'Sift in flour and salt, fold gently.',
        'Pour batter into greased ramekins.',
        'Bake for 12-14 minutes until edges are set but center is soft.',
        'Serve immediately with vanilla ice cream.'
      ],
      image: 'https://images.unsplash.com/photo-1578985545062-69928b1d9587?w=400&h=300&fit=crop',
      isFavorite: true,
    },
  ];

  // State management
  const [selectedCategory, setSelectedCategory] = useState('All');
  const [favorites, setFavorites] = useState({2: true, 4: true});
  const [selectedRecipe, setSelectedRecipe] = useState(null);
  const [modalVisible, setModalVisible] = useState(false);
  const [addRecipeModal, setAddRecipeModal] = useState(false);
  const [myRecipes, setMyRecipes] = useState([]);
  const [recipes, setRecipes] = useState(initialRecipes);
  
  // New recipe form state
  const [newRecipe, setNewRecipe] = useState({
    title: '',
    category: 'Italian',
    time: '',
    difficulty: 'Easy',
    servings: '',
    calories: '',
    ingredients: [''],
    instructions: [''],
    image: 'https://images.unsplash.com/photo-1546069901-ba9599a7e63c?w=400&h=300&fit=crop',
  });

  const filteredRecipes = selectedCategory === 'All' 
    ? [...recipes, ...myRecipes] 
    : [...recipes, ...myRecipes].filter(recipe => recipe.category === selectedCategory);

  const toggleFavorite = (recipeId) => {
    setFavorites(prev => ({
      ...prev,
      [recipeId]: !prev[recipeId]
    }));
  };

  const favoriteRecipes = [...recipes, ...myRecipes].filter(recipe => favorites[recipe.id]);

  const handleAddRecipe = () => {
    const newRecipeWithId = {
      ...newRecipe,
      id: Date.now(),
      isFavorite: false,
    };
    
    setMyRecipes(prev => [...prev, newRecipeWithId]);
    setAddRecipeModal(false);
    
    setNewRecipe({
      title: '',
      category: 'Italian',
      time: '',
      difficulty: 'Easy',
      servings: '',
      calories: '',
      ingredients: [''],
      instructions: [''],
      image: 'https://images.unsplash.com/photo-1546069901-ba9599a7e63c?w=400&h=300&fit=crop',
    });
  };

  const CategoryCard = ({ category }) => (
    <TouchableOpacity 
      style={[
        styles.categoryCard, 
        { 
          backgroundColor: selectedCategory === category.name ? category.color : '#FFF',
          borderWidth: selectedCategory === category.name ? 0 : 1,
          borderColor: '#E0E0E0'
        }
      ]}
      onPress={() => setSelectedCategory(category.name)}
    >
      <View style={[
        styles.categoryIcon,
        { backgroundColor: selectedCategory === category.name ? '#FFF' : category.color }
      ]}>
        <Ionicons 
          name={category.icon} 
          size={24} 
          color={selectedCategory === category.name ? category.color : '#FFF'} 
        />
      </View>
      <Text style={[
        styles.categoryName,
        { color: selectedCategory === category.name ? '#FFF' : '#333' }
      ]}>
        {category.name}
      </Text>
    </TouchableOpacity>
  );

  const RecipeCard = ({ recipe }) => {
    const isFav = favorites[recipe.id];
    const isMyRecipe = myRecipes.some(r => r.id === recipe.id);
    
    return (
      <TouchableOpacity 
        style={styles.recipeCard}
        onPress={() => {
          setSelectedRecipe(recipe);
          setModalVisible(true);
        }}
      >
        <Image source={{ uri: recipe.image }} style={styles.recipeImage} />
        {isMyRecipe && (
          <View style={styles.myRecipeBadge}>
            <Text style={styles.myRecipeText}>My Recipe</Text>
          </View>
        )}
        <View style={styles.recipeContent}>
          <Text style={styles.recipeTitle}>{recipe.title}</Text>
          <View style={styles.recipeDetails}>
            <View style={styles.detailItem}>
              <Ionicons name="time-outline" size={16} color="#666" />
              <Text style={styles.detailText}>{recipe.time}</Text>
            </View>
            <View style={styles.detailItem}>
              <Ionicons name="people-outline" size={16} color="#666" />
              <Text style={styles.detailText}>{recipe.servings} servings</Text>
            </View>
            <View style={styles.detailItem}>
              <Ionicons name="flame-outline" size={16} color="#666" />
              <Text style={styles.detailText}>{recipe.calories}</Text>
            </View>
          </View>
          <View style={styles.categoryBadge}>
            <Text style={styles.categoryText}>{recipe.category}</Text>
            <Text style={[styles.categoryText, {marginLeft: 8}]}>{recipe.difficulty}</Text>
          </View>
        </View>
        <TouchableOpacity 
          style={styles.favoriteButton}
          onPress={() => toggleFavorite(recipe.id)}
        >
          <Ionicons
            name={isFav ? 'heart' : 'heart-outline'}
            size={24}
            color={isFav ? '#FF6B6B' : '#666'}
          />
        </TouchableOpacity>
      </TouchableOpacity>
    );
  };

  const RecipeDetailModal = () => (
    <Modal
      animationType="slide"
      transparent={false}
      visible={modalVisible}
      onRequestClose={() => setModalVisible(false)}
    >
      {selectedRecipe && (
        <SafeAreaView style={styles.modalContainer}>
          <View style={styles.modalHeader}>
            <TouchableOpacity onPress={() => setModalVisible(false)}>
              <Ionicons name="close" size={28} color="#333" />
            </TouchableOpacity>
            <Text style={styles.modalTitle}>Recipe Details</Text>
            <TouchableOpacity onPress={() => toggleFavorite(selectedRecipe.id)}>
              <Ionicons
                name={favorites[selectedRecipe.id] ? 'heart' : 'heart-outline'}
                size={28}
                color={favorites[selectedRecipe.id] ? '#FF6B6B' : '#333'}
              />
            </TouchableOpacity>
          </View>
          
          <ScrollView>
            <Image source={{ uri: selectedRecipe.image }} style={styles.modalImage} />
            
            <View style={styles.modalContent}>
              <Text style={styles.modalRecipeTitle}>{selectedRecipe.title}</Text>
              <View style={styles.recipeMeta}>
                <View style={styles.metaItem}>
                  <Ionicons name="time-outline" size={20} color="#666" />
                  <Text style={styles.metaLabel}>Prep Time</Text>
                  <Text style={styles.metaValue}>{selectedRecipe.time}</Text>
                </View>
                <View style={styles.metaItem}>
                  <Ionicons name="people-outline" size={20} color="#666" />
                  <Text style={styles.metaLabel}>Servings</Text>
                  <Text style={styles.metaValue}>{selectedRecipe.servings}</Text>
                </View>
                <View style={styles.metaItem}>
                  <Ionicons name="flame-outline" size={20} color="#666" />
                  <Text style={styles.metaLabel}>Calories</Text>
                  <Text style={styles.metaValue}>{selectedRecipe.calories}</Text>
                </View>
                <View style={styles.metaItem}>
                  <Ionicons name="flag-outline" size={20} color="#666" />
                  <Text style={styles.metaLabel}>Difficulty</Text>
                  <Text style={styles.metaValue}>{selectedRecipe.difficulty}</Text>
                </View>
              </View>

              <Text style={styles.sectionTitleModal}>Ingredients</Text>
              {selectedRecipe.ingredients.map((ingredient, index) => (
                <View key={index} style={styles.ingredientItem}>
                  <Ionicons name="checkmark-circle" size={20} color="#4CAF50" />
                  <Text style={styles.ingredientText}>{ingredient}</Text>
                </View>
              ))}

              <Text style={styles.sectionTitleModal}>Instructions</Text>
              {selectedRecipe.instructions.map((step, index) => (
                <View key={index} style={styles.instructionStep}>
                  <View style={styles.stepNumber}>
                    <Text style={styles.stepNumberText}>{index + 1}</Text>
                  </View>
                  <Text style={styles.instructionText}>{step}</Text>
                </View>
              ))}
            </View>
          </ScrollView>
        </SafeAreaView>
      )}
    </Modal>
  );

  const AddRecipeModal = () => (
    <Modal
      animationType="slide"
      transparent={false}
      visible={addRecipeModal}
      onRequestClose={() => setAddRecipeModal(false)}
    >
      <SafeAreaView style={styles.modalContainer}>
        <View style={styles.modalHeader}>
          <TouchableOpacity onPress={() => setAddRecipeModal(false)}>
            <Ionicons name="close" size={28} color="#333" />
          </TouchableOpacity>
          <Text style={styles.modalTitle}>Add New Recipe</Text>
          <TouchableOpacity onPress={handleAddRecipe}>
            <Text style={styles.saveButton}>Save</Text>
          </TouchableOpacity>
        </View>
        
        <ScrollView style={styles.addRecipeForm}>
          <TextInput
            style={styles.input}
            placeholder="Recipe Title"
            value={newRecipe.title}
            onChangeText={(text) => setNewRecipe({...newRecipe, title: text})}
          />
          
          <Text style={styles.formLabel}>Category</Text>
          <ScrollView horizontal style={styles.categorySelector}>
            {categories.map(category => (
              <TouchableOpacity
                key={category.id}
                style={[
                  styles.categoryOption,
                  newRecipe.category === category.name && { backgroundColor: category.color }
                ]}
                onPress={() => setNewRecipe({...newRecipe, category: category.name})}
              >
                <Text style={[
                  styles.categoryOptionText,
                  newRecipe.category === category.name && { color: '#FFF' }
                ]}>
                  {category.name}
                </Text>
              </TouchableOpacity>
            ))}
          </ScrollView>

          <View style={styles.rowInputs}>
            <View style={styles.halfInput}>
              <Text style={styles.formLabel}>Prep Time</Text>
              <TextInput
                style={styles.input}
                placeholder="e.g., 30 min"
                value={newRecipe.time}
                onChangeText={(text) => setNewRecipe({...newRecipe, time: text})}
              />
            </View>
            <View style={styles.halfInput}>
              <Text style={styles.formLabel}>Servings</Text>
              <TextInput
                style={styles.input}
                placeholder="e.g., 4"
                value={newRecipe.servings}
                onChangeText={(text) => setNewRecipe({...newRecipe, servings: text})}
              />
            </View>
          </View>

          <View style={styles.rowInputs}>
            <View style={styles.halfInput}>
              <Text style={styles.formLabel}>Calories</Text>
              <TextInput
                style={styles.input}
                placeholder="e.g., 450 per serving"
                value={newRecipe.calories}
                onChangeText={(text) => setNewRecipe({...newRecipe, calories: text})}
              />
            </View>
            <View style={styles.halfInput}>
              <Text style={styles.formLabel}>Difficulty</Text>
              <View style={styles.difficultySelector}>
                {['Easy', 'Medium', 'Hard'].map(level => (
                  <TouchableOpacity
                    key={level}
                    style={[
                      styles.difficultyOption,
                      newRecipe.difficulty === level && styles.difficultySelected
                    ]}
                    onPress={() => setNewRecipe({...newRecipe, difficulty: level})}
                  >
                    <Text style={[
                      styles.difficultyText,
                      newRecipe.difficulty === level && styles.difficultyTextSelected
                    ]}>
                      {level}
                    </Text>
                  </TouchableOpacity>
                ))}
              </View>
            </View>
          </View>

          <Text style={styles.formLabel}>Ingredients (one per line)</Text>
          {newRecipe.ingredients.map((ingredient, index) => (
            <TextInput
              key={index}
              style={styles.input}
              placeholder={`Ingredient ${index + 1}`}
              value={ingredient}
              onChangeText={(text) => {
                const newIngredients = [...newRecipe.ingredients];
                newIngredients[index] = text;
                setNewRecipe({...newRecipe, ingredients: newIngredients});
              }}
            />
          ))}
          <TouchableOpacity
            style={styles.addButton}
            onPress={() => setNewRecipe({
              ...newRecipe,
              ingredients: [...newRecipe.ingredients, '']
            })}
          >
            <Ionicons name="add-circle" size={24} color="#4CAF50" />
            <Text style={styles.addButtonText}>Add Another Ingredient</Text>
          </TouchableOpacity>
          
          <Text style={styles.formLabel}>Instructions (one per line)</Text>
          {newRecipe.instructions.map((instruction, index) => (
            <TextInput
              key={index}
              style={[styles.input, styles.instructionInput]}
              placeholder={`Step ${index + 1}`}
              value={instruction}
              multiline
              onChangeText={(text) => {
                const newInstructions = [...newRecipe.instructions];
                newInstructions[index] = text;
                setNewRecipe({...newRecipe, instructions: newInstructions});
              }}
            />
          ))}
          <TouchableOpacity
            style={styles.addButton}
            onPress={() => setNewRecipe({
              ...newRecipe,
              instructions: [...newRecipe.instructions, '']
            })}
          >
            <Ionicons name="add-circle" size={24} color="#4CAF50" />
            <Text style={styles.addButtonText}>Add Another Step</Text>
          </TouchableOpacity>
        </ScrollView>
      </SafeAreaView>
    </Modal>
  );

  return (
    <SafeAreaView style={styles.container}>
      <ScrollView showsVerticalScrollIndicator={false}>
        <View style={styles.header}>
          <View>
            <Text style={styles.greeting}>FoodRecipe App 🍳</Text>
            <Text style={styles.subtitle}>Discover & Save Delicious Recipes</Text>
          </View>
          <TouchableOpacity style={styles.favoritesBadge}>
            <Ionicons name="heart" size={24} color="#FF6B6B" />
            <Text style={styles.favoritesCount}>{favoriteRecipes.length}</Text>
          </TouchableOpacity>
        </View>

        <Text style={styles.sectionTitle}>Categories ({categories.length})</Text>
        <ScrollView horizontal showsHorizontalScrollIndicator={false} style={styles.categoriesContainer}>
          <TouchableOpacity 
            style={[
              styles.categoryCard, 
              { 
                backgroundColor: selectedCategory === 'All' ? '#9E9E9E' : '#FFF',
                borderWidth: selectedCategory === 'All' ? 0 : 1,
              }
            ]}
            onPress={() => setSelectedCategory('All')}
          >
            <View style={[
              styles.categoryIcon,
              { backgroundColor: selectedCategory === 'All' ? '#FFF' : '#9E9E9E' }
            ]}>
              <Ionicons 
                name="apps" 
                size={24} 
                color={selectedCategory === 'All' ? '#9E9E9E' : '#FFF'} 
              />
            </View>
            <Text style={[
              styles.categoryName,
              { color: selectedCategory === 'All' ? '#FFF' : '#333' }
            ]}>
              All
            </Text>
          </TouchableOpacity>
          
          {categories.map(category => (
            <CategoryCard key={category.id} category={category} />
          ))}
        </ScrollView>

        <View style={styles.actionButtons}>
          <TouchableOpacity 
            style={styles.actionButton}
            onPress={() => {
              setSelectedCategory('All');
            }}
          >
            <Ionicons name="book" size={20} color="#FFF" />
            <Text style={styles.actionButtonText}>My Recipes ({myRecipes.length})</Text>
          </TouchableOpacity>
          
          <TouchableOpacity 
            style={[styles.actionButton, styles.addButtonAction]}
            onPress={() => setAddRecipeModal(true)}
          >
            <Ionicons name="add-circle" size={20} color="#FFF" />
            <Text style={styles.actionButtonText}>Add Recipe</Text>
          </TouchableOpacity>
        </View>

        {favoriteRecipes.length > 0 && (
          <>
            <Text style={styles.sectionTitle}>My Favorites ({favoriteRecipes.length})</Text>
            <ScrollView horizontal showsHorizontalScrollIndicator={false} style={styles.categoriesContainer}>
              {favoriteRecipes.map(recipe => (
                <TouchableOpacity 
                  key={recipe.id} 
                  style={styles.favoriteRecipeCard}
                  onPress={() => {
                    setSelectedRecipe(recipe);
                    setModalVisible(true);
                  }}
                >
                  <Image source={{ uri: recipe.image }} style={styles.favoriteImage} />
                  <View style={styles.favoriteOverlay}>
                    <Text style={styles.favoriteTitle}>{recipe.title}</Text>
                  </View>
                  <View style={styles.favoriteHeart}>
                    <Ionicons name="heart" size={20} color="#FF6B6B" />
                  </View>
                </TouchableOpacity>
              ))}
            </ScrollView>
          </>
        )}

        <Text style={styles.sectionTitle}>
          {selectedCategory === 'All' ? 'All Recipes' : selectedCategory} 
          ({filteredRecipes.length})
        </Text>
        {filteredRecipes.length > 0 ? (
          filteredRecipes.map(recipe => (
            <RecipeCard key={recipe.id} recipe={recipe} />
          ))
        ) : (
          <View style={styles.emptyState}>
            <Ionicons name="restaurant-outline" size={60} color="#E0E0E0" />
            <Text style={styles.emptyStateText}>No recipes found</Text>
            <Text style={styles.emptyStateSubtext}>Try a different category or add a new recipe</Text>
          </View>
        )}
      </ScrollView>

      <RecipeDetailModal />
      <AddRecipeModal />
    </SafeAreaView>
  );
}

const styles = StyleSheet.create({
  container: { flex: 1, backgroundColor: '#F7F7F7' },
  header: { 
    flexDirection: 'row', 
    justifyContent: 'space-between', 
    alignItems: 'center',
    paddingHorizontal: 20, 
    paddingTop: 20, 
    paddingBottom: 10 
  },
  greeting: { fontSize: 28, fontWeight: 'bold', color: '#333' },
  subtitle: { fontSize: 16, color: '#666', marginTop: 4 },
  favoritesBadge: { 
    flexDirection: 'row', 
    alignItems: 'center',
    backgroundColor: '#FFF',
    paddingHorizontal: 12,
    paddingVertical: 6,
    borderRadius: 20,
    elevation: 2
  },
  favoritesCount: { 
    marginLeft: 4, 
    fontSize: 16, 
    fontWeight: 'bold', 
    color: '#FF6B6B' 
  },
  sectionTitle: { 
    fontSize: 22, 
    fontWeight: 'bold', 
    color: '#333', 
    marginHorizontal: 20, 
    marginTop: 20, 
    marginBottom: 10 
  },
  categoriesContainer: { 
    paddingHorizontal: 20,
    paddingBottom: 10
  },
  categoryCard: { 
    width: 100, 
    height: 120, 
    borderRadius: 16, 
    padding: 12, 
    marginRight: 12, 
    justifyContent: 'center', 
    alignItems: 'center',
    elevation: 2,
    shadowColor: '#000',
    shadowOffset: { width: 0, height: 2 },
    shadowOpacity: 0.1,
    shadowRadius: 4,
  },
  categoryIcon: { 
    width: 50, 
    height: 50, 
    borderRadius: 25, 
    justifyContent: 'center', 
    alignItems: 'center', 
    marginBottom: 8 
  },
  categoryName: { 
    fontSize: 14, 
    fontWeight: '600', 
    textAlign: 'center' 
  },
  actionButtons: {
    flexDirection: 'row',
    marginHorizontal: 20,
    marginTop: 10,
    marginBottom: 20,
  },
  actionButton: {
    flex: 1,
    flexDirection: 'row',
    alignItems: 'center',
    justifyContent: 'center',
    backgroundColor: '#4ECDC4',
    paddingVertical: 12,
    paddingHorizontal: 16,
    borderRadius: 12,
    marginRight: 10,
  },
  addButtonAction: {
    backgroundColor: '#FF6B6B',
    marginRight: 0,
  },
  actionButtonText: {
    color: '#FFF',
    fontWeight: 'bold',
    marginLeft: 8,
  },
  recipeCard: { 
    backgroundColor: '#FFF', 
    borderRadius: 12, 
    marginHorizontal: 20, 
    marginBottom: 16, 
    overflow: 'hidden',
    elevation: 3,
    shadowColor: '#000',
    shadowOffset: { width: 0, height: 2 },
    shadowOpacity: 0.1,
    shadowRadius: 4,
    position: 'relative',
  },
  myRecipeBadge: {
    position: 'absolute',
    top: 10,
    left: 10,
    backgroundColor: '#4CAF50',
    paddingHorizontal: 10,
    paddingVertical: 4,
    borderRadius: 12,
    zIndex: 1,
  },
  myRecipeText: {
    color: '#FFF',
    fontSize: 12,
    fontWeight: 'bold',
  },
  recipeImage: { 
    width: '100%', 
    height: 180 
  },
  recipeContent: { 
    padding: 16 
  },
  recipeTitle: { 
    fontSize: 20, 
    fontWeight: 'bold', 
    marginBottom: 12, 
    color: '#333' 
  },
  recipeDetails: { 
    flexDirection: 'row', 
    justifyContent: 'space-between', 
    marginBottom: 12 
  },
  detailItem: { 
    flexDirection: 'row', 
    alignItems: 'center' 
  },
  detailText: { 
    marginLeft: 4, 
    fontSize: 14, 
    color: '#666' 
  },
  categoryBadge: { 
    flexDirection: 'row',
    backgroundColor: '#F0F0F0', 
    borderRadius: 20, 
    paddingHorizontal: 12, 
    paddingVertical: 6, 
    alignSelf: 'flex-start' 
  },
  categoryText: { 
    fontSize: 12, 
    color: '#666', 
    fontWeight: '500' 
  },
  favoriteButton: { 
    position: 'absolute', 
    top: 10, 
    right: 10, 
    backgroundColor: 'rgba(255, 255, 255, 0.9)', 
    borderRadius: 20, 
    padding: 8 
  },
  favoriteRecipeCard: {
    width: 160,
    height: 120,
    borderRadius: 12,
    marginRight: 12,
    overflow: 'hidden',
    position: 'relative'
  },
  favoriteImage: {
    width: '100%',
    height: '100%'
  },
  favoriteOverlay: {
    position: 'absolute',
    bottom: 0,
    left: 0,
    right: 0,
    backgroundColor: 'rgba(0,0,0,0.7)',
    padding: 8
  },
  favoriteTitle: {
    color: '#FFF',
    fontSize: 14,
    fontWeight: 'bold'
  },
  favoriteHeart: {
    position: 'absolute',
    top: 8,
    right: 8,
    backgroundColor: 'rgba(255,255,255,0.9)',
    borderRadius: 12,
    padding: 4
  },
  emptyState: {
    alignItems: 'center',
    justifyContent: 'center',
    padding: 40,
    marginHorizontal: 20,
    backgroundColor: '#FFF',
    borderRadius: 12,
  },
  emptyStateText: {
    fontSize: 18,
    fontWeight: 'bold',
    color: '#666',
    marginTop: 16,
  },
  emptyStateSubtext: {
    fontSize: 14,
    color: '#999',
    marginTop: 8,
    textAlign: 'center',
  },
  modalContainer: { flex: 1, backgroundColor: '#FFF' },
  modalHeader: {
    flexDirection: 'row',
    justifyContent: 'space-between',
    alignItems: 'center',
    paddingHorizontal: 20,
    paddingVertical: 15,
    borderBottomWidth: 1,
    borderBottomColor: '#F0F0F0'
  },
  modalTitle: { fontSize: 20, fontWeight: 'bold', color: '#333' },
  saveButton: {
    fontSize: 16,
    fontWeight: 'bold',
    color: '#4CAF50',
  },
  modalImage: { width: '100%', height: 250 },
  modalContent: { padding: 20 },
  modalRecipeTitle: { 
    fontSize: 28, 
    fontWeight: 'bold', 
    color: '#333', 
    marginBottom: 20 
  },
  recipeMeta: {
    flexDirection: 'row',
    justifyContent: 'space-between',
    flexWrap: 'wrap',
    marginBottom: 30,
    backgroundColor: '#F9F9F9',
    padding: 15,
    borderRadius: 12
  },
  metaItem: {
    alignItems: 'center',
    width: '48%',
    marginBottom: 10
  },
  metaLabel: {
    fontSize: 12,
    color: '#888',
    marginTop: 4,
    marginBottom: 2
  },
  metaValue: {
    fontSize: 16,
    fontWeight: 'bold',
    color: '#333'
  },
  sectionTitleModal: {
    fontSize: 22,
    fontWeight: 'bold',
    color: '#333',
    marginTop: 20,
    marginBottom: 15
  },
  ingredientItem: {
    flexDirection: 'row',
    alignItems: 'center',
    marginBottom: 10,
    paddingVertical: 8,
    paddingHorizontal: 12,
    backgroundColor: '#F9F9F9',
    borderRadius: 8
  },
  ingredientText: {
    fontSize: 16,
    color: '#333',
    marginLeft: 10,
    flex: 1
  },
  instructionStep: {
    flexDirection: 'row',
    marginBottom: 20,
    alignItems: 'flex-start'
  },
  stepNumber: {
    width: 30,
    height: 30,
    borderRadius: 15,
    backgroundColor: '#FF6B6B',
    justifyContent: 'center',
    alignItems: 'center',
    marginRight: 15,
    marginTop: 2
  },
  stepNumberText: {
    color: '#FFF',
    fontWeight: 'bold',
    fontSize: 16
  },
  instructionText: {
    fontSize: 16,
    color: '#333',
    lineHeight: 24,
    flex: 1
  },
  addRecipeForm: {
    padding: 20,
  },
  input: {
    backgroundColor: '#F9F9F9',
    padding: 15,
    borderRadius: 10,
    marginBottom: 15,
    fontSize: 16,
  },
  formLabel: {
    fontSize: 16,
    fontWeight: 'bold',
    color: '#333',
    marginBottom: 8,
  },
  rowInputs: {
    flexDirection: 'row',
    justifyContent: 'space-between',
    marginBottom: 15,
  },
  halfInput: {
    width: '48%',
  },
  categorySelector: {
    marginBottom: 20,
  },
  categoryOption: {
    paddingHorizontal: 15,
    paddingVertical: 8,
    borderRadius: 20,
    backgroundColor: '#F0F0F0',
    marginRight: 10,
    marginBottom: 10,
  },
  categoryOptionText: {
    fontSize: 14,
    color: '#666',
  },
  difficultySelector: {
    flexDirection: 'row',
    justifyContent: 'space-between',
  },
  difficultyOption: {
    flex: 1,
    paddingVertical: 10,
    alignItems: 'center',
    backgroundColor: '#F0F0F0',
    marginHorizontal: 4,
    borderRadius: 8,
  },
  difficultySelected: {
    backgroundColor: '#4CAF50',
  },
  difficultyText: {
    fontSize: 14,
    color: '#666',
  },
  difficultyTextSelected: {
    color: '#FFF',
    fontWeight: 'bold',
  },
  addButton: {
    flexDirection: 'row',
    alignItems: 'center',
    justifyContent: 'center',
    padding: 12,
    backgroundColor: '#F0F0F0',
    borderRadius: 10,
    marginBottom: 20,
  },
  addButtonText: {
    marginLeft: 8,
    fontSize: 16,
    color: '#4CAF50',
    fontWeight: 'bold',
  },
  instructionInput: {
    minHeight: 60,
    textAlignVertical: 'top',
  },
});
