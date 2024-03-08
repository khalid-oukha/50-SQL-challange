-- --------------------------------------------------------
-- Hôte:                         127.0.0.1
-- Version du serveur:           8.0.30 - MySQL Community Server - GPL
-- SE du serveur:                Win64
-- HeidiSQL Version:             12.1.0.6537
-- --------------------------------------------------------

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET NAMES utf8 */;
/*!50503 SET NAMES utf8mb4 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;


-- Listage de la structure de la base pour evento
CREATE DATABASE IF NOT EXISTS `evento` /*!40100 DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci */ /*!80016 DEFAULT ENCRYPTION='N' */;
USE `evento`;

-- Listage de la structure de table evento. categories
CREATE TABLE IF NOT EXISTS `categories` (
  `id` bigint unsigned NOT NULL AUTO_INCREMENT,
  `name` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `image` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `description` text COLLATE utf8mb4_unicode_ci,
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Listage des données de la table evento.categories : ~0 rows (environ)
INSERT INTO `categories` (`id`, `name`, `image`, `description`, `created_at`, `updated_at`) VALUES
	(1, 'youcode', '1709653186youcode.jpg', 'dadaadadadadad', '2024-03-05 14:39:46', '2024-03-05 14:39:46');

-- Listage de la structure de table evento. events
CREATE TABLE IF NOT EXISTS `events` (
  `id` bigint unsigned NOT NULL AUTO_INCREMENT,
  `title` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `image` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `description` text COLLATE utf8mb4_unicode_ci NOT NULL,
  `date` date NOT NULL,
  `location` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `capacity` int NOT NULL,
  `availableSeats` int DEFAULT NULL,
  `status` enum('pending','active','cancelled') COLLATE utf8mb4_unicode_ci NOT NULL,
  `category_id` bigint unsigned NOT NULL,
  `organizer_id` bigint unsigned NOT NULL,
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT NULL,
  `reservation_type` enum('auto','manual') COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT 'auto',
  PRIMARY KEY (`id`),
  KEY `events_category_id_foreign` (`category_id`),
  KEY `events_organizer_id_foreign` (`organizer_id`),
  CONSTRAINT `events_category_id_foreign` FOREIGN KEY (`category_id`) REFERENCES `categories` (`id`) ON DELETE CASCADE,
  CONSTRAINT `events_organizer_id_foreign` FOREIGN KEY (`organizer_id`) REFERENCES `organizers` (`user_id`) ON DELETE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=31 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Listage des données de la table evento.events : ~14 rows (environ)
INSERT INTO `events` (`id`, `title`, `image`, `description`, `date`, `location`, `capacity`, `availableSeats`, `status`, `category_id`, `organizer_id`, `created_at`, `updated_at`, `reservation_type`) VALUES
	(1, 'Tucker Cooke', '1709656125.jpg', 'Rerum quod vero aute', '2024-03-22', 'Leah Robbins', 144, 45, 'active', 1, 23, '2024-03-05 15:28:45', '2024-03-07 08:37:30', 'auto'),
	(12, 'youcode events', '1709672105.jpg', 'youcode events youcode events youcode events', '2024-03-05', 'youcode events youcode events', 55, 55, 'pending', 1, 23, '2024-03-05 19:55:05', '2024-03-05 19:55:05', 'auto'),
	(17, 'Family Fun for Sure!', '1709716837.png', 'Family Fun for Sure! Whole family went. City had a very fun energy for the few days we were there. Medina is so quaint and full of great food choices. Performances were beautiful. The teens especially loved it, as did I. Hope to go again.', '2024-03-30', 'Zelenia Sharpe', 15, 11, 'active', 1, 24, '2024-03-06 08:20:37', '2024-03-06 14:15:27', 'auto'),
	(18, 'Essaouira Exclusive Dune Buggy Adventure', '1709717304.jpg', 'An unforgettable buggy rollercoaster (but you\'re driving it!) that combines the thrill of off-roading with the beauty of Essaouira\'s landscapes. This tour is designed for everyone, whether you\'re a seasoned driver or', '2024-03-21', 'Live guide: Arabic, Russian, English, French', 15, 14, 'active', 1, 24, '2024-03-06 08:28:24', '2024-03-07 12:11:48', 'auto'),
	(19, 'best event created', '1709762304.jpg', 'best event created v best event created', '2024-03-31', 'youcode events youcode events', 14, 14, 'pending', 1, 24, '2024-03-06 20:58:25', '2024-03-06 20:58:25', 'auto'),
	(20, 'dadad', 'C:\\Users\\Youcode\\AppData\\Local\\Temp\\php9A61.tmp', 'dadadadadadadadad', '2024-03-30', 'Zelenia Sharpe', 155, 155, 'pending', 1, 24, '2024-03-06 21:02:23', '2024-03-06 21:02:24', 'auto'),
	(21, 'Thomas Brown', 'C:\\Users\\Youcode\\AppData\\Local\\Temp\\phpFCDC.tmp', 'Elit quibusdam porr', '2024-03-31', 'Octavia Macdonald', 555, 555, 'pending', 1, 24, '2024-03-06 21:04:59', '2024-03-06 21:04:59', 'auto'),
	(22, 'Tamekah Ford', '1709763061.jpg', 'Quod debitis quibusd', '2024-03-24', 'Alexis Livingston', 45, 44, 'pending', 1, 24, '2024-03-06 21:11:01', '2024-03-07 12:11:48', 'auto'),
	(23, 'hasaaaan event', '1709764820.png', 'Qui dolore nostrum o', '2024-03-30', 'Ciaran Kelley', 10, 10, 'pending', 1, 24, '2024-03-06 21:40:20', '2024-03-06 21:40:20', 'manual'),
	(24, 'aaaaaaaaaaaaaa', '1709765845.webp', 'dadadada aaaaaaaaaaaaaaaaaaaaaa', '2024-03-21', 'aaaaaaaaaaaaaaaaaaa', 14, 14, 'pending', 1, 24, '2024-03-06 21:57:25', '2024-03-06 21:57:25', 'manual'),
	(25, 'alalala', '1709765968.jpg', 'alalala', '2024-03-06', 'alalala', 55, 55, 'active', 1, 24, '2024-03-06 21:59:28', '2024-03-06 22:01:46', 'manual'),
	(26, 'Rhea Blanchard', '1709818205.jpg', 'Mollit rem laudantiu', '2024-03-29', 'Riley Holloway', 1, 0, 'active', 1, 24, '2024-03-07 12:30:06', '2024-03-07 12:31:03', 'auto'),
	(27, 'Maile Small', '1709818477.jpg', 'Sed adipisicing rati', '2024-03-07', 'Teegan Osborne', 1, 0, 'active', 1, 24, '2024-03-07 12:34:37', '2024-03-07 12:36:35', 'auto'),
	(28, 'mm', '1709818594.png', 'mmmmm', '2024-03-07', 'dazdzazdz', 1, 1, 'pending', 1, 24, '2024-03-07 12:36:34', '2024-03-07 12:36:34', 'auto');

-- Listage de la structure de table evento. failed_jobs
CREATE TABLE IF NOT EXISTS `failed_jobs` (
  `id` bigint unsigned NOT NULL AUTO_INCREMENT,
  `uuid` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `connection` text COLLATE utf8mb4_unicode_ci NOT NULL,
  `queue` text COLLATE utf8mb4_unicode_ci NOT NULL,
  `payload` longtext COLLATE utf8mb4_unicode_ci NOT NULL,
  `exception` longtext COLLATE utf8mb4_unicode_ci NOT NULL,
  `failed_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  UNIQUE KEY `failed_jobs_uuid_unique` (`uuid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Listage des données de la table evento.failed_jobs : ~0 rows (environ)

-- Listage de la structure de table evento. migrations
CREATE TABLE IF NOT EXISTS `migrations` (
  `id` int unsigned NOT NULL AUTO_INCREMENT,
  `migration` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `batch` int NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=16 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Listage des données de la table evento.migrations : ~0 rows (environ)
INSERT INTO `migrations` (`id`, `migration`, `batch`) VALUES
	(1, '2014_10_12_000000_create_users_table', 1),
	(2, '2014_10_12_100000_create_password_reset_tokens_table', 1),
	(3, '2019_08_19_000000_create_failed_jobs_table', 1),
	(4, '2019_12_14_000001_create_personal_access_tokens_table', 1),
	(5, '2024_03_03_222748_create_roles_table', 1),
	(6, '2024_03_03_223518_create_role_user_table', 1),
	(7, '2024_03_03_225830_create_categories_table', 1),
	(8, '2024_03_03_230903_create_organizers_table', 1),
	(9, '2024_03_03_231912_create_events_table', 1),
	(10, '2024_03_03_233131_create_reservations_table', 1),
	(11, '2024_03_03_234611_create_tickets_table', 1),
	(12, '2024_03_04_082558_create_permissions_table', 1),
	(13, '2024_03_04_082929_create_users_permissions_table', 1),
	(14, '2024_03_04_083217_create_roles_permissions_table', 1),
	(15, '2024_03_06_214632_add_reservation_type_to_events_table', 2);

-- Listage de la structure de table evento. organizers
CREATE TABLE IF NOT EXISTS `organizers` (
  `user_id` bigint unsigned NOT NULL,
  `cin` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `phone_number` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `profile_picture` varchar(255) COLLATE utf8mb4_unicode_ci DEFAULT NULL,
  `bio` text COLLATE utf8mb4_unicode_ci,
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT NULL,
  PRIMARY KEY (`user_id`),
  CONSTRAINT `organizers_user_id_foreign` FOREIGN KEY (`user_id`) REFERENCES `users` (`id`) ON DELETE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Listage des données de la table evento.organizers : ~13 rows (environ)
INSERT INTO `organizers` (`user_id`, `cin`, `phone_number`, `profile_picture`, `bio`, `created_at`, `updated_at`) VALUES
	(13, 'PA724247', '209.797.4051', 'https://via.placeholder.com/640x480.png/00dd55?text=dolorem', 'Reprehenderit sit possimus iusto velit et. Optio quibusdam atque in corporis officiis est omnis.', '2024-03-05 14:22:06', '2024-03-05 14:22:06'),
	(14, 'PA286168', '586-893-8969', 'https://via.placeholder.com/640x480.png/00aa33?text=ducimus', 'Provident minus assumenda ab voluptatem quas. Numquam deserunt dolorem rerum quia corporis quia est. Quo sit tempora qui voluptas ratione dolorum libero aliquid. Sapiente sed autem aliquid ut.', '2024-03-05 14:22:06', '2024-03-05 14:22:06'),
	(15, 'PA859075', '+1 (623) 845-1635', 'https://via.placeholder.com/640x480.png/004422?text=consequatur', 'Quia qui commodi in id. Reprehenderit et eveniet nihil non explicabo provident voluptatem.', '2024-03-05 14:22:06', '2024-03-05 14:22:06'),
	(16, 'PA230848', '+17752840069', 'https://via.placeholder.com/640x480.png/003344?text=aut', 'Unde rerum vel et incidunt atque. Quas consequatur dolores nulla quo alias ut aut. Ea harum accusamus et officiis quae doloremque.', '2024-03-05 14:22:06', '2024-03-05 14:22:06'),
	(17, 'PA830656', '831-777-3804', 'https://via.placeholder.com/640x480.png/007755?text=neque', 'Et eum aperiam quos voluptatem ex. Aliquam hic reiciendis animi aliquam. Modi at amet saepe id autem.', '2024-03-05 14:22:06', '2024-03-05 14:22:06'),
	(18, 'PA517845', '719-316-5420', 'https://via.placeholder.com/640x480.png/00dd66?text=voluptatem', 'Rerum ex dignissimos non ut iste dolore consequatur. Velit pariatur eligendi adipisci aperiam soluta doloremque laboriosam. Voluptas omnis consequatur et enim sed ipsam. Animi repellat sapiente numquam.', '2024-03-05 14:22:06', '2024-03-05 14:22:06'),
	(19, 'PA422911', '+1.989.324.2669', 'https://via.placeholder.com/640x480.png/00eeff?text=et', 'Temporibus qui omnis quam nesciunt. Sint itaque in cumque laboriosam odit quidem magnam ipsam. Omnis repellendus consequatur tempora quia qui quibusdam.', '2024-03-05 14:22:06', '2024-03-05 14:22:06'),
	(20, 'PA965327', '219.514.8007', 'https://via.placeholder.com/640x480.png/00eeee?text=sapiente', 'Dolorem consectetur quia aperiam et. Et maiores eos placeat placeat in. Officiis ut hic consectetur. Placeat cupiditate odit est consequatur pariatur voluptates dolores.', '2024-03-05 14:22:06', '2024-03-05 14:22:06'),
	(21, 'PA055201', '217-729-9093', 'https://via.placeholder.com/640x480.png/008844?text=voluptatibus', 'Optio ullam delectus necessitatibus nisi necessitatibus. Quae dolorem velit ab consequatur. Non repellat et labore voluptatem sint quis quo. Itaque quia reprehenderit magni non maxime.', '2024-03-05 14:22:06', '2024-03-05 14:22:06'),
	(22, 'PA999428', '(458) 424-6789', 'https://via.placeholder.com/640x480.png/00bbee?text=excepturi', 'Aut ducimus reiciendis iste molestiae delectus repellendus tenetur. Vel est ut sit reiciendis libero qui.', '2024-03-05 14:22:06', '2024-03-05 14:22:06'),
	(23, 'pa333333', '4576644129', '1709653345-4576644129.jpg', 'addaad', '2024-03-05 14:42:25', '2024-03-05 14:42:25'),
	(24, 'pa333333', '0696367649', '1709716046-0696367649.jpg', 'The Lorm alphabet is a method of tactile signing named after Hieronymus Lorm, who developed it in the late 19th century. Letters are spelled by tapping or ...', '2024-03-06 08:07:26', '2024-03-06 08:07:26'),
	(26, 'pa333333', '0696367649', '1709730804-0696367649.png', 'dadza', '2024-03-06 12:13:24', '2024-03-06 12:13:24');

-- Listage de la structure de table evento. password_reset_tokens
CREATE TABLE IF NOT EXISTS `password_reset_tokens` (
  `email` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `token` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `created_at` timestamp NULL DEFAULT NULL,
  PRIMARY KEY (`email`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Listage des données de la table evento.password_reset_tokens : ~0 rows (environ)

-- Listage de la structure de table evento. permissions
CREATE TABLE IF NOT EXISTS `permissions` (
  `id` bigint unsigned NOT NULL AUTO_INCREMENT,
  `name` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Listage des données de la table evento.permissions : ~2 rows (environ)
INSERT INTO `permissions` (`id`, `name`, `created_at`, `updated_at`) VALUES
	(1, 'create-event', '2024-03-05 14:22:05', '2024-03-05 14:22:05'),
	(2, 'create-user', '2024-03-05 14:22:05', '2024-03-05 14:22:05');

-- Listage de la structure de table evento. personal_access_tokens
CREATE TABLE IF NOT EXISTS `personal_access_tokens` (
  `id` bigint unsigned NOT NULL AUTO_INCREMENT,
  `tokenable_type` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `tokenable_id` bigint unsigned NOT NULL,
  `name` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `token` varchar(64) COLLATE utf8mb4_unicode_ci NOT NULL,
  `abilities` text COLLATE utf8mb4_unicode_ci,
  `last_used_at` timestamp NULL DEFAULT NULL,
  `expires_at` timestamp NULL DEFAULT NULL,
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `personal_access_tokens_token_unique` (`token`),
  KEY `personal_access_tokens_tokenable_type_tokenable_id_index` (`tokenable_type`,`tokenable_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Listage des données de la table evento.personal_access_tokens : ~0 rows (environ)

-- Listage de la structure de table evento. reservations
CREATE TABLE IF NOT EXISTS `reservations` (
  `id` bigint unsigned NOT NULL AUTO_INCREMENT,
  `user_id` bigint unsigned NOT NULL,
  `event_id` bigint unsigned NOT NULL,
  `number_of_seats` int NOT NULL DEFAULT '1',
  `status` enum('pending','confirmed','cancelled') COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT 'pending',
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `reservations_user_id_foreign` (`user_id`),
  KEY `reservations_event_id_foreign` (`event_id`),
  CONSTRAINT `reservations_event_id_foreign` FOREIGN KEY (`event_id`) REFERENCES `events` (`id`) ON DELETE CASCADE,
  CONSTRAINT `reservations_user_id_foreign` FOREIGN KEY (`user_id`) REFERENCES `users` (`id`) ON DELETE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=17 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Listage des données de la table evento.reservations : ~11 rows (environ)
INSERT INTO `reservations` (`id`, `user_id`, `event_id`, `number_of_seats`, `status`, `created_at`, `updated_at`) VALUES
	(1, 24, 17, 1, 'confirmed', NULL, NULL),
	(2, 26, 17, 1, 'cancelled', NULL, '2024-03-07 16:05:11'),
	(3, 16, 17, 1, 'confirmed', NULL, '2024-03-08 07:14:29'),
	(4, 15, 17, 1, 'cancelled', NULL, '2024-03-07 16:05:18'),
	(5, 16, 12, 1, 'confirmed', '2024-03-07 09:17:10', '2024-03-07 09:17:10'),
	(6, 5, 12, 1, 'pending', '2024-03-07 09:17:10', '2024-03-07 09:17:10'),
	(7, 24, 12, 1, 'pending', '2024-03-07 09:17:10', '2024-03-07 09:17:10'),
	(8, 24, 18, 1, 'confirmed', '2024-03-07 09:17:10', '2024-03-07 16:31:27'),
	(9, 24, 22, 1, 'confirmed', '2024-03-07 09:19:39', '2024-03-07 09:19:39'),
	(13, 24, 26, 1, 'confirmed', '2024-03-07 12:30:46', '2024-03-07 12:30:46'),
	(14, 24, 27, 1, 'confirmed', '2024-03-07 12:35:34', '2024-03-07 12:35:34');

-- Listage de la structure de table evento. roles
CREATE TABLE IF NOT EXISTS `roles` (
  `id` bigint unsigned NOT NULL AUTO_INCREMENT,
  `name` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Listage des données de la table evento.roles : ~2 rows (environ)
INSERT INTO `roles` (`id`, `name`, `created_at`, `updated_at`) VALUES
	(1, 'admin', '2024-03-05 14:22:05', '2024-03-05 14:22:05'),
	(2, 'organizer', '2024-03-05 14:22:05', '2024-03-05 14:22:05'),
	(3, 'spectator', '2024-03-05 14:22:05', '2024-03-05 14:22:05');

-- Listage de la structure de table evento. roles_permissions
CREATE TABLE IF NOT EXISTS `roles_permissions` (
  `role_id` bigint unsigned NOT NULL,
  `permission_id` bigint unsigned NOT NULL,
  KEY `roles_permissions_role_id_foreign` (`role_id`),
  KEY `roles_permissions_permission_id_foreign` (`permission_id`),
  CONSTRAINT `roles_permissions_permission_id_foreign` FOREIGN KEY (`permission_id`) REFERENCES `permissions` (`id`) ON DELETE CASCADE,
  CONSTRAINT `roles_permissions_role_id_foreign` FOREIGN KEY (`role_id`) REFERENCES `roles` (`id`) ON DELETE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Listage des données de la table evento.roles_permissions : ~6 rows (environ)
INSERT INTO `roles_permissions` (`role_id`, `permission_id`) VALUES
	(1, 1),
	(1, 1),
	(2, 1),
	(2, 1),
	(3, 2),
	(3, 2);

-- Listage de la structure de table evento. role_user
CREATE TABLE IF NOT EXISTS `role_user` (
  `user_id` bigint unsigned NOT NULL,
  `role_id` bigint unsigned NOT NULL,
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT NULL,
  PRIMARY KEY (`user_id`,`role_id`),
  KEY `role_user_role_id_foreign` (`role_id`),
  CONSTRAINT `role_user_role_id_foreign` FOREIGN KEY (`role_id`) REFERENCES `roles` (`id`) ON DELETE CASCADE,
  CONSTRAINT `role_user_user_id_foreign` FOREIGN KEY (`user_id`) REFERENCES `users` (`id`) ON DELETE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Listage des données de la table evento.role_user : ~5 rows (environ)
INSERT INTO `role_user` (`user_id`, `role_id`, `created_at`, `updated_at`) VALUES
	(11, 1, NULL, NULL),
	(12, 2, NULL, NULL),
	(23, 2, NULL, NULL),
	(24, 2, NULL, NULL),
	(25, 3, NULL, NULL),
	(26, 2, NULL, NULL),
	(27, 1, NULL, NULL),
	(28, 3, NULL, NULL);

-- Listage de la structure de table evento. tickets
CREATE TABLE IF NOT EXISTS `tickets` (
  `id` bigint unsigned NOT NULL AUTO_INCREMENT,
  `reservation_id` bigint unsigned NOT NULL,
  `user_id` bigint unsigned NOT NULL,
  `ticket_number` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `status` enum('issued','used','cancelled') COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT 'issued',
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `tickets_ticket_number_unique` (`ticket_number`),
  KEY `tickets_reservation_id_foreign` (`reservation_id`),
  KEY `tickets_user_id_foreign` (`user_id`),
  CONSTRAINT `tickets_reservation_id_foreign` FOREIGN KEY (`reservation_id`) REFERENCES `reservations` (`id`) ON DELETE CASCADE,
  CONSTRAINT `tickets_user_id_foreign` FOREIGN KEY (`user_id`) REFERENCES `users` (`id`) ON DELETE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Listage des données de la table evento.tickets : ~0 rows (environ)

-- Listage de la structure de table evento. users
CREATE TABLE IF NOT EXISTS `users` (
  `id` bigint unsigned NOT NULL AUTO_INCREMENT,
  `lastname` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `firstname` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `email` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `email_verified_at` timestamp NULL DEFAULT NULL,
  `password` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `remember_token` varchar(100) COLLATE utf8mb4_unicode_ci DEFAULT NULL,
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `users_email_unique` (`email`)
) ENGINE=InnoDB AUTO_INCREMENT=29 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Listage des données de la table evento.users : ~27 rows (environ)
INSERT INTO `users` (`id`, `lastname`, `firstname`, `email`, `email_verified_at`, `password`, `remember_token`, `created_at`, `updated_at`) VALUES
	(1, 'Jonathan Bergstrom', 'Collin Tremblay', 'cristal33@example.net', '2024-03-05 14:22:05', '$2y$12$azcPR1Vt6d7Guxyk8l5KHu4m847woAT1DaGdTPZS1Uu32CI0wlks2', 'S8DAhKCytB', '2024-03-05 14:22:05', '2024-03-05 14:22:05'),
	(2, 'Mr. Arnaldo Gaylord II', 'Freeda Wisozk', 'maiya27@example.org', '2024-03-05 14:22:05', '$2y$12$azcPR1Vt6d7Guxyk8l5KHu4m847woAT1DaGdTPZS1Uu32CI0wlks2', 'xY5LDskXt4', '2024-03-05 14:22:05', '2024-03-05 14:22:05'),
	(3, 'Issac Beahan', 'Jack Tremblay', 'dana15@example.net', '2024-03-05 14:22:05', '$2y$12$azcPR1Vt6d7Guxyk8l5KHu4m847woAT1DaGdTPZS1Uu32CI0wlks2', 'GjoNCc6Bpp', '2024-03-05 14:22:05', '2024-03-05 14:22:05'),
	(4, 'Dejah Hahn', 'Celine Graham', 'bode.tanner@example.com', '2024-03-05 14:22:05', '$2y$12$azcPR1Vt6d7Guxyk8l5KHu4m847woAT1DaGdTPZS1Uu32CI0wlks2', 'XTy3uXA98E', '2024-03-05 14:22:05', '2024-03-05 14:22:05'),
	(5, 'Gertrude Lubowitz I', 'Keely Satterfield', 'kailey.murphy@example.org', '2024-03-05 14:22:05', '$2y$12$azcPR1Vt6d7Guxyk8l5KHu4m847woAT1DaGdTPZS1Uu32CI0wlks2', 'pyPqW2E8cq', '2024-03-05 14:22:05', '2024-03-05 14:22:05'),
	(6, 'Royce Dickens', 'Emie McCullough', 'brock.breitenberg@example.net', '2024-03-05 14:22:05', '$2y$12$azcPR1Vt6d7Guxyk8l5KHu4m847woAT1DaGdTPZS1Uu32CI0wlks2', 'gLfjrPyStr', '2024-03-05 14:22:05', '2024-03-05 14:22:05'),
	(7, 'Ms. Kristin Ledner Jr.', 'Prof. Santiago Bernhard II', 'williamson.ocie@example.com', '2024-03-05 14:22:05', '$2y$12$azcPR1Vt6d7Guxyk8l5KHu4m847woAT1DaGdTPZS1Uu32CI0wlks2', 'zuBYKdEsr6', '2024-03-05 14:22:05', '2024-03-05 14:22:05'),
	(8, 'Eloise Williamson', 'Pattie Aufderhar', 'muhammad17@example.net', '2024-03-05 14:22:05', '$2y$12$azcPR1Vt6d7Guxyk8l5KHu4m847woAT1DaGdTPZS1Uu32CI0wlks2', 'gnEqwbfphR', '2024-03-05 14:22:05', '2024-03-05 14:22:05'),
	(9, 'Bryana O\'Reilly', 'Cecile Harber', 'walker.glenna@example.org', '2024-03-05 14:22:05', '$2y$12$azcPR1Vt6d7Guxyk8l5KHu4m847woAT1DaGdTPZS1Uu32CI0wlks2', 'xZ6cVh0dvn', '2024-03-05 14:22:05', '2024-03-05 14:22:05'),
	(10, 'Caesar Stokes', 'Reed Bogisich', 'heidenreich.maia@example.com', '2024-03-05 14:22:05', '$2y$12$azcPR1Vt6d7Guxyk8l5KHu4m847woAT1DaGdTPZS1Uu32CI0wlks2', '8p2MLBYyCB', '2024-03-05 14:22:05', '2024-03-05 14:22:05'),
	(11, 'Admin', 'Admin', 'admin1@example.com', NULL, '$2y$12$1GywOB/nYjkv1i2xGEHMiO2NM0lJkF5rGIPlIS.NaqvKkVEjod.pS', NULL, '2024-03-05 14:22:05', '2024-03-05 14:22:05'),
	(12, 'User', 'User', 'user1@gmail.com', NULL, '$2y$12$kDB/DUnP/gA6I/SGMQdujukX8zZKHY8U4uy7gyci2zlBTxurZXfcS', NULL, '2024-03-05 14:22:06', '2024-03-05 14:22:06'),
	(13, 'Kathryn Lueilwitz', 'London Ziemann', 'rschmeler@example.net', '2024-03-05 14:22:06', '$2y$12$azcPR1Vt6d7Guxyk8l5KHu4m847woAT1DaGdTPZS1Uu32CI0wlks2', 'JOMf0wgGC4', '2024-03-05 14:22:06', '2024-03-05 14:22:06'),
	(14, 'Prof. Remington Douglas Sr.', 'Joy Kihn', 'jedediah.schaden@example.net', '2024-03-05 14:22:06', '$2y$12$azcPR1Vt6d7Guxyk8l5KHu4m847woAT1DaGdTPZS1Uu32CI0wlks2', 'UxiiG6wKQL', '2024-03-05 14:22:06', '2024-03-05 14:22:06'),
	(15, 'Summer Kris III', 'Dr. Alberto Abbott II', 'dewayne11@example.com', '2024-03-05 14:22:06', '$2y$12$azcPR1Vt6d7Guxyk8l5KHu4m847woAT1DaGdTPZS1Uu32CI0wlks2', 'moJ0UU9VU9', '2024-03-05 14:22:06', '2024-03-05 14:22:06'),
	(16, 'Giovanna Fisher DDS', 'Adrianna Cartwright', 'juvenal.altenwerth@example.net', '2024-03-05 14:22:06', '$2y$12$azcPR1Vt6d7Guxyk8l5KHu4m847woAT1DaGdTPZS1Uu32CI0wlks2', 'on2o2AMk25', '2024-03-05 14:22:06', '2024-03-05 14:22:06'),
	(17, 'Trisha Bechtelar', 'Ethyl Mante', 'jacobs.sherwood@example.net', '2024-03-05 14:22:06', '$2y$12$azcPR1Vt6d7Guxyk8l5KHu4m847woAT1DaGdTPZS1Uu32CI0wlks2', 'BeTfqKuCt1', '2024-03-05 14:22:06', '2024-03-05 14:22:06'),
	(18, 'Paris Barrows Jr.', 'Mr. Brycen Robel II', 'herdman@example.com', '2024-03-05 14:22:06', '$2y$12$azcPR1Vt6d7Guxyk8l5KHu4m847woAT1DaGdTPZS1Uu32CI0wlks2', '0JlHGWzGfi', '2024-03-05 14:22:06', '2024-03-05 14:22:06'),
	(19, 'Vesta Berge', 'Bruce Kunde', 'ybergstrom@example.com', '2024-03-05 14:22:06', '$2y$12$azcPR1Vt6d7Guxyk8l5KHu4m847woAT1DaGdTPZS1Uu32CI0wlks2', 'eaXZCEuLpH', '2024-03-05 14:22:06', '2024-03-05 14:22:06'),
	(20, 'Miss Andreanne Morissette III', 'Dr. Jo Pacocha PhD', 'evie.spencer@example.com', '2024-03-05 14:22:06', '$2y$12$azcPR1Vt6d7Guxyk8l5KHu4m847woAT1DaGdTPZS1Uu32CI0wlks2', '7Z1Y9u8rug', '2024-03-05 14:22:06', '2024-03-05 14:22:06'),
	(21, 'Danny Wiza', 'Miss Lea Kub', 'raymundo.schneider@example.net', '2024-03-05 14:22:06', '$2y$12$azcPR1Vt6d7Guxyk8l5KHu4m847woAT1DaGdTPZS1Uu32CI0wlks2', 'Y2QxC3HfbE', '2024-03-05 14:22:06', '2024-03-05 14:22:06'),
	(22, 'Carlo Bahringer', 'Dr. Mabel Bayer', 'kenyon.monahan@example.com', '2024-03-05 14:22:06', '$2y$12$azcPR1Vt6d7Guxyk8l5KHu4m847woAT1DaGdTPZS1Uu32CI0wlks2', 'iKwSDuRJdg', '2024-03-05 14:22:06', '2024-03-05 14:22:06'),
	(23, 'Cantu', 'Liberty', 'habe@mailinator.com', NULL, '$2y$12$5ZHs4LWMnVffWF0mzAfuLOBdlc9kJ7cP9heVQL1nM2QG.wgSY9TGO', NULL, '2024-03-05 14:41:33', '2024-03-05 14:41:33'),
	(24, 'moumni', 'zaid', 'zaidmo@gmail.com', NULL, '$2y$12$4CPv2zHNydKjqjXPZ/9pWeXOsWWmjNUkIiMhtUnCIAtckCw1JsmtC', NULL, '2024-03-06 08:05:59', '2024-03-06 08:05:59'),
	(25, 'Stuart', 'Keelie', 'wabyd@mailinator.com', NULL, '$2y$12$yGczXO1EGq1.6emMiLrH2.AIn2gMTveb8fdH/1PmazrDC2uW8ZiSu', NULL, '2024-03-06 12:12:53', '2024-03-06 12:12:53'),
	(26, 'Yates', 'Taylor', 'wyqin@mailinator.com', NULL, '$2y$12$AF1eBvR4dO5li5GNaQx.e.wnryRtfIKpruD3xr0BDXG/CPe8tdcje', NULL, '2024-03-06 12:13:09', '2024-03-06 12:13:09'),
	(27, 'admin@admin.com', 'admin@admin.com', 'admin@admin.com', NULL, 'admin@admin.com', NULL, NULL, NULL),
	(28, 'dadadadad', 'ddada', 'oukhakhalid@gmail.com', NULL, '$2y$12$Nq10ZFsMw7izIGd7kIAsJ./31xfEaWXIbXyLsb0VoQ9fnaQBiJVB.', NULL, '2024-03-08 10:49:00', '2024-03-08 10:49:00');

-- Listage de la structure de table evento. users_permissions
CREATE TABLE IF NOT EXISTS `users_permissions` (
  `user_id` bigint unsigned NOT NULL,
  `permission_id` bigint unsigned NOT NULL,
  KEY `users_permissions_user_id_foreign` (`user_id`),
  KEY `users_permissions_permission_id_foreign` (`permission_id`),
  CONSTRAINT `users_permissions_permission_id_foreign` FOREIGN KEY (`permission_id`) REFERENCES `permissions` (`id`) ON DELETE CASCADE,
  CONSTRAINT `users_permissions_user_id_foreign` FOREIGN KEY (`user_id`) REFERENCES `users` (`id`) ON DELETE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Listage des données de la table evento.users_permissions : ~0 rows (environ)
INSERT INTO `users_permissions` (`user_id`, `permission_id`) VALUES
	(12, 2);

/*!40103 SET TIME_ZONE=IFNULL(@OLD_TIME_ZONE, 'system') */;
/*!40101 SET SQL_MODE=IFNULL(@OLD_SQL_MODE, '') */;
/*!40014 SET FOREIGN_KEY_CHECKS=IFNULL(@OLD_FOREIGN_KEY_CHECKS, 1) */;
/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40111 SET SQL_NOTES=IFNULL(@OLD_SQL_NOTES, 1) */;
